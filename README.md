# Client-server_architecture
HTTP ( Idempotent and safety methods, status codes, request/response structure), rich client, thin client, HTTPS, API, REST, SOAP, XML, JSON
 ## 1. Что такое клиент серверная архитектура?

> Архитектура компьютерной сети, в которой множество клиентов (удаленных процессоров) запрашивают и получают данные от централизованного сервера (хост-компьютера). 
Клиентские компьютеры предоставляют интерфейс, позволяющий пользователю компьютера запрашивать услуги сервера и отображать результаты, возвращаемые сервером.   

 ## 2. Что такое толстый клиент?

> Это рабочая машина или ПК, которые функционируют на основе своей ОС и наполнены полноценным набором ПО для требуемых задач пользователя. Выполняет запрашиваемые со стороны пользователя манипуляции независимо от ведущего сервера.

***Преимущества толстых клиентов:***

- Большая функциональность;
- Наличие многопользовательского режима;
- Возможность работы в режиме оффлайн;
- Мгновенное быстродействие;
- Минимальная зависимость от сложных серверов.

***Недочеты:***

- Все рабочие машины на постоянной основе нуждаются в техническом обслуживании;
- Нужда в индивидуальном обновлении аппаратного ПО каждого клиента до уровня программного обеспечения, которое будет использоваться;
- Массивные объемы дистрибутивов;
- Полная зависимость от платформ, под которую данные клиенты были созданы.

**Примеры: Office 365, Microsoft Outlook, Приложение для сканирования документов, для записи экрана(FreeCam, BandiCam) и др.**

 ## 3. Что  такое тонкий клиент?

> Вид клиента, который может переносить выполнение задач по обработке информации на сервер, не применяя свои мощности по вычислению для их внедрения.

***Плюсы тонкого клиента:***

- Минимальное аппаратное обслуживание;
- Низкий риск возникновения неисправности;
- Минимальные технические требования к аппаратному оборудованию.

***Негативные стороны:***

- При сбое на сервере «пострадают» все подключенные пользователи;
- Нет возможности работать без активного подключения к сети;
- При взаимодействии с большим массивом данных может снижаться объем производительности основного сервера.

**Примеры: Веб-браузеры и веб-приложения, наподобие WP, Google Docs, онлайн-игры**

 ## 4. Какие HTTP коды ответа сервера которые понимаете?
**1 xx — информация**
```
Эти коды состояния HTTP обозначают предварительный ответ. 
Клиентский компьютер получит один или несколько ответов 1 xx, прежде чем получить обычный ответ.
```
- 100 — продолжение.
- 101 — смена протоколов.

**2 xx — запрос принят**
```
Эти коды состояния HTTP указывают на успешное принятие сервером запроса.
```
- 200 — ОК. Запрос клиента выполнен успешно.
- 201 — создан.
- 202 — принято.
- 203 — недостоверные сведения.
- 204 — содержимое отсутствует.
- 205 — сброс содержимого.
- 206 — частичное содержимое.

**3 xx — перенаправление**
```
Эти коды состояния HTTP указывают на необходимость выполнения клиентским браузером дополнительных действий для выполнения запроса. 
Например, клиентскому браузеру может потребоваться запросить другую страницу на сервере. Или же повторить запрос, используя прокси-сервер.
```
- 301 — перемещено навсегда.
- 302 — объект перемещен.
- 304 — объект не изменялся.

**4 xx — ошибка клиента**
```
Эти коды состояния HTTP указывают на возникновение ошибки, вероятно, на стороне клиентского браузера. 
Например, клиентский браузер мог запросить несуществующую страницу. Или не предоставить достоверные сведения для проверки подлинности.
```
- 400 — неверный запрос. Серверу не удалось распознать запрос из-за ошибки в синтаксисе. Клиенту не следует повторять запрос без внесения изменений.
- 401 — доступ запрещен(неавторизованый).
- 403 — запрет.
- 404 — объект не найден.

**5 xx — ошибка сервера**
```
Эти коды состояния HTTP указывают на невозможность выполнения сервером запроса из-за того, что сервер сталкивается с ошибкой.
```
- 500 — внутренняя ошибка сервера.
- 501 — значения, указанные в заголовке, определяют нереализованную конфигурацию.
- 502 — веб-сервером в качестве шлюза или прокси-сервера получен недопустимый ответ.
- 503 — служба недоступна

 ## 5. Что такое API ?

***Application Programming Interface(API)*** - тип программного интерфейса, предоставляющего услуги другим программам, с помощью которого две и больше программ(систем) могут взаимодействовать друг с другом


 ## 6. Что такое Rest Api ?

***REST(Representational State Transfer) API*** - архитектурный стиль, который обеспечивает общение клента с сервером с помощью HTTP запросов (GET, POST, PUT, DELETE etc.)


 ## 7. Перечислите требования к архитектуре REST
- Единый интерфейс
> Ресурсы должны быть однозначно идентифицированы посредством одного URL-адреса и только с помощью базовых методов сетевого протокола (DELETE, PUT, GET, POST и др.)
- Разграничение клиента и сервера

- Нет сохранения состояния
> В период между запросами клиента никакая информация о состоянии клиента на сервере не хранится. Все запросы от клиента должны быть составлены так, чтобы сервер получил всю необходимую информацию для выполнения запроса. Состояние сессии при этом сохраняется на стороне клиента

- Кэширование всегда разрешено
> Процесс сохранения некоторых ответов на клиенте или на посреднике для сокращения времени ответа сервера. ***Например***, *вы заходите на веб-сайт с общими изображениями верхнего и нижнего колонтитулов на каждой странице. Каждый раз, когда вы посещаете новую страницу веб-сайта, сервер должен повторно отправлять одни и те же изображения. Чтобы избежать этого, клиент кэширует или сохраняет эти изображения после первого ответа, а затем использует изображения из кэша.*

- Многоуровневая система
> Клиент обычно не способен точно определить взаимодействует ли он напрямую с сервером, или же с промежуточным узлом в связи иерархической структурой сетей (слои)

- Код предоставляется по запросу.
> Серверы могут временно расширять или настраивать функциональные возможности клиента, передавая код программного обеспечения. ***Например*** *когда вы заполняете регистрационную форму на каком-либо веб-сайте, ваш браузер сразу же выделяет все допущенные ошибки (например, неверные номера телефонов). Это происходит благодаря коду, отправленному сервером.*

## 8. Что такое HTTP/HTTPS ?
> ***HTTP (от англ. HyperText Transfer Protocol)*** ― это протокол передачи данных в интернете. С его помощью браузер получает информацию от сервера и показывает пользователю контент. Это первый протокол, который создали для работы в веб-пространстве

> ***HTTPS (аббр. от англ. HyperText Transfer Protocol Secure)*** — расширение протокола HTTP для поддержки шифрования в целях повышения безопасности. HTTPS не является отдельным протоколом. Это обычный HTTP, работающий через шифрованные транспортные механизмы SSL и TLS.

## 9. Из чего состоит Запрос HTTP ?
- Метод запрос ( GET, HEAD, PUT, POST, TRACE, OPTIONS, DELETE и др. )
- Версия протокола ( HTTP 1.0 ; HTTP/1.1 ; HTTP/2.0 )
- Хост (URL)
- Header (Content-Type, Content-Length, User-Agent, Token и др.)
- Body ***(optional)***

## 10. Из чего состоит Ответ HTTP ?
- Версия протокола ( HTTP 1.0 ; HTTP/1.1 ; HTTP/2.0 )
- Статус код (200 OK, 404 Not Found, 500 Internal Server Error)
- Header (Content-Type, Content-Length, Server, Date, Cache-Control, Set-Cookie и др.)
- Body

## 11. Какие знаете методы HTTP ?
> GET
>> позволяет получить информацию от сервера

> POST
>> позволяет отправить информацию на сервер

> PUT
>> позволяет изменить ранее отправленные на сервер данные 

> DELETE
>> позволяет удалить ранее отправленные на сервер данные 

> HEAD
>> позволяет получить информацию от сервера в виде заголовков(без тела)

> CONNECT
>> позволяет создать сетевое соединения между двумя компьютерами в условиях ограниченного сетевого подключения

> OPTIONS
>> позволяет получить настройки сервера(какие запросы сервер может обрабатывать)

> TRACE
>> позволяет проверить связь с целевым ресурсом(используеться для отладки обратной связи)

> PATCH
>> позволяет изменить определенную часть ранее отправленных на сервер данных

## 12. Что такое CRUD ?
> Аббревиатура из четырех слов, которые обозначают четыре базовые, стандартные операции выполняемие сервером

- С - Create - создание, отправка информации на сервер (POST)
- R - Read - чтение, получение информации с сервера (GET, HEAD, OPTIONS)
- U - Update - видоизменение ранее отправленой информации на сервер (PUT, PATCH)
- D - Delete - удаление ранее отправленой информации на сервер (DELETE)


## 13. Что такое Идемпотентность ?
> Метод, при котором повторный, идентичный запрос, имеет один и тот же результат, не меняющий состояния сервера ***(Отправили запрос первый раз, при втором таком же запросе на сервере ничего не поменяеться)***

## 14. Какие методы, из которых вы перечислили являются Идемтопотентными?
GET, PUT, HEAD, DELETE, OPTIONS, TRACE

## 15. Какие методы, из которых вы перечислили являются Безопасными?
> Метод HTTP является **безопасным**, если он не меняет состояние сервера. Другими словами, безопасный метод проводит операции **"только чтение" (read-only).** 
 
**Безопасные:**  
GET, OPTIONS, TRACE, HEAD, CONNECT

## 16. Что такое XML ?
> **eXtensible Markup Language** — расширяемый язык разметки. Используется для хранения и передачи данных.

- В XML каждый элемент должен быть заключен в теги — некий текст, обернутый в угловые скобки **<>**
- Базовый елемент XML документа состоит из открывающегося тега **<Full_name>**, сообщения внутри **Soltys Vladyslav Igorevich**, закрывающегося тега </**Full_name>**
- Строка, числовое или boolean значение пишуться внутри тегов без кавычек
- Значение null отображаеться одним закрывающимся тегом **<pet_3/>**
- Документ начинаеться и заканчиваеться корневым тегом(елементом)
- Тег внутри может содержать аттрибуты **version="1.0" encoding="UTF-8"**

```
<?xml version="1.0" encoding="UTF-8" ?>
<root>
  <Full_name>Soltys Vladyslav Igorevich</Full_name>
  <Age>24</Age>
  <Number_of_pets>
    <pet_1>Foggy</pet_1>
    <pet_2>Rocky</pet_2>
    <pet_3/>
  </Number_of_pets>
  <Future_desired_salary>800-1000$</Future_desired_salary>
  <skills_to_be_learned_today>What is a client-server architecture</skills_to_be_learned_today>
  <skills_to_be_learned_today>HTTP Methods of requests to the server</skills_to_be_learned_today>
  <skills_to_be_learned_today>HTTP server response codes</skills_to_be_learned_today>
  <skills_to_be_learned_today>Structures of HTTP requests and responses</skills_to_be_learned_today>
</root>
```


## 17. Что такое JSON ?
 > Tекстовый формат обмена данными, основанный на JavaScript

**Пример:**
```
{
  "Full_name": "Soltys Vladyslav Igorevich",
  "Age": 24,
  "Number_of_pets": {
    "pet_1": "Foggy",
    "pet_2": "Rocky",
    "pet_3": "Dafny"
  },
  "Future_desired_salary": "800-1000$",
  "skills_to_be_learned_today": [
    "What is a client-server architecture",
    "HTTP Methods of requests to the server",
    "HTTP server response codes",
    "Structures of HTTP requests and responses"
  ]
}
```

В качестве значений в JSON могут быть использованы:

- **запись** — это неупорядоченное множество пар **ключ:значение**, заключённое в фигурные скобки **«{ }»**. Ключ описывается строкой, между ним и значением стоит символ **«:»**. Пары ключ-значение отделяются друг от друга запятыми.
- **массив (одномерный)** — это упорядоченное множество значений. Массив заключается в квадратные скобки **«[ ]»**. Значения разделяются запятыми. Массив может быть пустым, то есть не содержать ни одного значения. Значения в пределах одного массива могут иметь разный тип.
число (целое или вещественное).
- **литералы** true (логическое значение «истина»), false (логическое значение «ложь») и null.
- **строка** — это упорядоченное множество из нуля или более символов юникода, заключённое в двойные кавычки.

## 18. Приведи пример, в чем отличие между XML/JSON ?
- XML - язык разметки.  JSON - формат, написанный на JavaScript
- XML - данные хранятся в виде древовидной структуры. JSON - данные хранятся в формате "ключ: значение"
- XML - Может выполнять обработку и форматирование документов и объектов. JSON - Не выполняет никакой обработки или вычислений
-  XML - Громоздкий и медленный синтаксический анализ. JSON - Очень быстро, поскольку размер файла значительно мал
- XML - Напрямую не поддерживает массивы. JSON - Поддерживает массив
- XML -Поддерживает множество сложных типов данных, включая диаграммы, изображения и другие непримитивные типы данных.  JSON - поддерживает только строки, числа, массивы, логические значения и объекты. Объекты могут содержать только примитивные типы.
- XML - поддерживает кодировки UTF-8 и UTF-16.  JSON -  поддерживает кодировки UTF, а также ASCII.
