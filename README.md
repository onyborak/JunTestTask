### Описание задачи
Необходимо разработать консольное приложение телефонная книга.

При запуске приложения должна открываться консоль с меню - действия, доступные с АК:
1. Вывести все записи.
2. Создать новую запись.
3. Отредактировать запись.
4. Удалить запись.
5. Вывести определенную запись

В каждой записи должен быть идентификатор, номер и имя.
Вся книга должна храниться в файловой системе на диске, в одном файле. Формат данных - json.


Структура проекта должна быть следующей:
1. Интерфейсный класс Tm_PhoneBoolInterface. В проекте он уже добавен и в нем созданы необходимые методы.
В этой же файле есть структура, представляющую одну запись в телефонной книге (Tm_Contact) и enum En_ResultCode - перечисление
раличных кодов выполнения функции интерфейса. Если метод завершился успешно, необходимо вернуть Ok и доп данные, если они подразумеваются
2. Реализация адресной книги должна быть в Tm_FilesPhoneBook. Внутри необходимо реализовать чтение книги из файла,
ее парсинг, изменение и сохранение обратно в файл.
3. Всю бизнес логику приложения необходимо реализовать в файле main.cpp. По идее это должен быть цикл, в котором происходит ввод данных в консоль,
анализ, выполнение какого-то действия с PhoneBook и вывод результата пользователю в консоль.


### Сборка
В CMakeLists.txt уже добавлена библиотека для работы с json. Поэтому, чтобы собрать проект, помимо стандартных g++,
cmake в систему необходимо установить libjsoncpp-dev.
Для сборки проекта, необходимо создать внутри папку build, перейти в нее и далее:
1. Запустить cmake: `cmake ../`. Он сгенерирует MakeFile
2. Запустить makefile: `make`. Он в итоге соберет бинарь

### Форматирование
В корень проекта добавлен .clang-format - это файлик с настройками форматирования кода. Необходим,
чтобы при разработке разными людьми в разных IDE и с разными вероисповеданиями был единый формат.
Большинство IDE его подхватывают и сами форматируют вводимый код в соответсвии с настройками.
Но чтобы отформатировать вручную - необходимо в корне проекта вызывать следующую команду:  
`find ./ -iname *.h -o -iname *.cpp -o -iname *.hpp | xargs clang-format -i`  
Утилита clang-format подхватит конфиг, лежащий в корне, и отформатирует переданные ему файлы.

