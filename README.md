# Лабораторная работа

# Сатторов Давлат

## Задание 1

Скачал виртуальную машину и дал пользователю права администратора (рис. 1).

<div align="center">
   <img src="https://github.com/user-attachments/assets/9b470c1d-4801-4d28-9956-905bc7f54215" alt="" width="500">
   <p>Рисунок 1 - Создание пользователя ВМ</p>
</div>

Скачал гостевые дополнения путём нажатия на: "Устройства" -> "Подключить образ диска Дополнений гостевой ОС", после чего дожидался окончания загрузки и перезагрузил ВМ (рис. 2).

<div align="center">
   <img src="https://github.com/user-attachments/assets/b4b77dbd-dd98-41ba-b6c7-e9bc4dd9ca3d" alt="" width="500">
   <p>Рисунок 2 - Подключение гостевых дополнений</p>
</div>

Теперь прописываю команды лабораторных работ.

```bash
sudo yum install wget
```

- sudo - команда, которая предоставляет права суперпользователя (администратора) для выполнения команды
- yum - система управления пакетами в дистрибутивах на базе Red Hat (например, CentOS, RHEL)
- install - параметр yum, который устанавливает указанный пакет программного обеспечения
- wget - название пакета, который будет установлен (утилита для загрузки файлов с сетей HTTP/HTTPS)

Команда успешно установилась, потому что дал пользователю, во время создания ВМ, права администратора (рис. 3).

<div align="center">
   <img src="https://github.com/user-attachments/assets/b2018e40-9fdb-47b5-aed6-c4ef3700d5a5" alt="" width="500">
   <p>Рисунок 3 - wget</p>
</div>

## Задание 2

```bash
sudo yum install curl
```

- sudo - команда для выполнения операции с правами суперпользователя (администратора)
- yum - система управления пакетами в дистрибутивах на базе Red Hat (например, CentOS, RHEL)
- install - параметр yum, указывающий на установку нового программного пакета
- curl - название пакета, который будет установлен (утилита для передачи данных с сервера на клиент и обратно через различные протоколы)

Скачал успешно `curl` (рис. 1).

<div align="center">
   <img src="https://github.com/user-attachments/assets/aad9362a-6f60-4620-bcb3-ad6d2db035e6" alt="" width="500">
   <p>Рисунок 1 - curl</p>
</div>

```bash
sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo
```

- sudo - команда для выполнения операции с правами суперпользователя (администратора)
- wget - утилита для загрузки файлов с сетей HTTP/HTTPS
- -P - параметр wget, указывающий директорию для сохранения загруженного файла
- /etc/yum.repos.d/ - целевая директория, куда будет сохранён загруженный файл (репозиторий для системы управления пакетами)
- `https://download.docker.com/linux/centos/docker-ce.repo` - URL-адрес файла репозитория Docker, который будет загружен

Успешно скачал файл Docker (рис. 2).

<div align="center">
   <img src="https://github.com/user-attachments/assets/cfd803d1-5a7a-4093-9300-bde6cc4ad10c" alt="" width="500">
   <p>Рисунок 2 - Docker</p>
</div>

```bash
sudo yum install docker-ce docker-ce-cli containerd.io
```

- sudo - команда для выполнения операции с правами суперпользователя (администратора)
- yum - система управления пакетами в дистрибутивах на базе Red Hat (например, CentOS, RHEL)
- install - параметр yum, указывающий на установку новых программных пакетов
- docker-ce - основной пакет Docker Community Edition (бесплатная версия Docker)
- docker-ce-cli - пакет, содержащий командную строку клиента Docker
- containerd.io - пакет службы containerd, которая является низкоуровневой системой управления контейнерами, используемой Docker

Эта команда устанавливает три ключевых компонента Docker: сам Docker (Community Edition), его командную строку и службу containerd, необходимую для работы с контейнерами (рис. 3).

<div align="center">
   <img src="https://github.com/user-attachments/assets/f70352c5-67b6-4396-812f-447fd7f76be9" alt="" width="500">
   <p>Рисунок 3 - Компоненты Docker</p>
</div>

```bash
sudo systemctl enable docker --now
```

- sudo - команда для выполнения операции с правами суперпользователя (администратора)
- systemctl - утилита для управления системными службами (демонами) в Linux
- enable - параметр systemctl, который включает службу для автоматического запуска при старте системы
- docker - название службы, которую необходимо включить (демон Docker)
- --now - параметр, указывающий на немедленный запуск службы, помимо её включения при загрузке системы

Эта команда включает службу Docker для автозапуска при старте системы и сразу запускает её в текущий момент (рис. 4).

<div align="center">
   <img src="https://github.com/user-attachments/assets/3a082508-e11d-4c8d-922f-d67405c5455f" alt="" width="1000">
   <p>Рисунок 4 - Автозапуск</p>
</div>

## Задание 3

```bash
COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)
```

- COMVER= - переменная COMVER, которой присваивается значение результата выполнения команды
- curl - утилита для запроса данных из указанного URL
- -s - параметр curl, подавляющий вывод прогресса (silent mode)
- `https://api.github.com/repos/docker/compose/releases/latest` - URL API GitHub для получения информации о последней версии Docker Compose
- | - труба (pipe), передающая вывод одной команды в качестве входных данных для следующей команды
- grep 'tag_name' - команда для поиска строки, содержащей "tag_name" (помечает версию релиза)
- cut -d\" -f4 - команда cut с разделителем "\"" и выборкой четвертого поля, чтобы извлечь чистый номер версии

Эта команда получает последнюю версию Docker Compose с помощью API GitHub, находит строку с названием тега релиза и извлекает чистый номер версии, записывая его в переменную `COMVER` (рис. 1).

<div align="center">
   <img src="https://github.com/user-attachments/assets/4354d555-0ccd-4431-be72-7677d17e01ce" alt="" width="1000">
   <p>Рисунок 1 - Версия Docker</p>
</div>

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose
```

- sudo - команда для выполнения операции с правами суперпользователя (администратора)
- curl - утилита для передачи данных через сетевые протоколы
- -L - параметр curl, который позволяет следовать переадресациям (редиректам), если они есть
- `https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)` - URL для загрузки Docker Compose:
  - `$COMVER` — переменная, содержащая версию Docker Compose, полученную ранее
  - `$(uname -s)` — команда, возвращающая название операционной системы (например, Linux)
  - `$(uname -m)` — команда, возвращающая архитектуру процессора (например, x86_64)
- -o /usr/bin/docker-compose - параметр curl, указывающий имя выходного файла, куда будет сохранён скачанный бинарный файл (в данном случае `/usr/bin/docker-compose`)

Эта команда загружает бинарный файл Docker Compose соответствующей версии и архитектуры с GitHub и сохраняет его в `/usr/bin/docker-compose`, что делает его доступным глобально в системе (рис. 2).

<div align="center">
   <img src="https://github.com/user-attachments/assets/0dde70b9-903c-4440-9f43-b32967e4cdfc" alt="" width="1000">
   <p>Рисунок 2 - Файл Docker Compose</p>
</div>

```bash
sudo chmod +x /usr/bin/docker-compose
```

- sudo - команда для выполнения операции с правами суперпользователя (администратора)
- chmod - утилита для изменения прав доступа к файлам и директориям
- +x - параметр chmod, который добавляет право на исполнение (execute) для указанного файла
- /usr/bin/docker-compose - путь к файлу, для которого изменяются права доступа

Эта команда добавляет право на выполнение файлу `/usr/bin/docker-compose`, делая его исполняемым, чтобы пользователи могли запускать Docker Compose как команду в системе (рис. 3).

<div align="center">
   <img src="https://github.com/user-attachments/assets/58d0d6e5-9229-432f-89e5-d456974510f4" alt="" width="1000">
   <p>Рисунок 3 - Команда для Docker Compose</p>
</div>

```bash
docker-compose --version
```

- docker-compose - команда для запуска утилиты Docker Compose, которая используется для определения и запуска многоконтейнерных приложений Docker
- --version - параметр, который выводит текущую версию установленного Docker Compose

Эта команда проверяет установленную версию Docker Compose, отображая её в консоли. Это помогает убедиться, что утилита успешно установлена и работает корректно (рис. 4).

<div align="center">
   <img src="https://github.com/user-attachments/assets/9be1bf7d-11a6-4a88-9b87-9da134a86f6a" alt="" width="1000">
   <p>Рисунок 4 - Версия Docker Compose</p>
</div>

```bash
sudo yum install git
```

- sudo - команда для выполнения операции с правами суперпользователя (администратора)
- yum - система управления пакетами в дистрибутивах на базе Red Hat (например, CentOS, RHEL)
- install - параметр yum, указывающий на установку нового программного пакета
- git - название пакета, который будет установлен (система контроля версий Git)

Эта команда устанавливает систему контроля версий Git с помощью менеджера пакетов `yum`, предоставляя права суперпользователя для выполнения операции (рис. 5).

<div align="center">
   <img src="https://github.com/user-attachments/assets/3f3f479b-f99f-482b-bf7f-20e8e82a3214" alt="" width="1000">
   <p>Рисунок 5 - Установка git</p>
</div>

```bash
git clone https://github.com/skl256/grafana_stack_for_docker.git
```

- git - команда для работы с системой контроля версий Git
- clone - параметр git, используемый для клонирования (скачивания) репозитория с удаленного сервера на локальную машину
- `https://github.com/skl256/grafana_stack_for_docker.git` - URL репозитория GitHub, который будет склонирован

Эта команда создает локальную копию репозитория `grafana_stack_for_docker` с GitHub, скачивая все его файлы и историю изменений в текущую директорию (рис. 6).

<div align="center">
   <img src="https://github.com/user-attachments/assets/3678f0fd-dc42-4cc5-9c51-19bd03225cba" alt="" width="1000">
   <p>Рисунок 6 - Директория</p>
</div>

```bash
cd grafana_stack_for_docker
```

- cd - команда для смены текущей директории в терминале
- grafana_stack_for_docker - название директории, в которую нужно перейти

Эта команда меняет текущую директорию на `grafana_stack_for_docker`, чтобы работать с файлами, склонированными из репозитория (рис. 7).

<div align="center">
   <img src="https://github.com/user-attachments/assets/4eb54797-1dbc-4234-bdee-77ae9bf5e2b1" alt="" width="1000">
   <p>Рисунок 7 - Переход в директорию</p>
</div>

```bash
sudo mkdir -p /mnt/common_volume/swarm/grafana/config
```

- sudo - команда для выполнения операции с правами суперпользователя (администратора)
- mkdir - утилита для создания новой директории
- -p - параметр mkdir, который позволяет создавать родительские директории при их отсутствии
- /mnt/common_volume/swarm/grafana/config - путь к новой директории, которую нужно создать

Эта команда создает вложенные директории по указанному пути `/mnt/common_volume/swarm/grafana/config`, при этом все промежуточные каталоги также будут созданы, если они еще не существуют (рис. 8).

<div align="center">
   <img src="https://github.com/user-attachments/assets/4f1373ff-ff7f-435e-a65b-62525989dc7c" alt="" width="1000">
   <p>Рисунок 8 - Создание новых директорий</p>
</div>

```bash
sudo mkdir -p /mnt/common_volume/grafana/{grafana-config,grafana-data,prometheus-data}
```

- sudo - команда для выполнения операции с правами суперпользователя (администратора)
- mkdir - утилита для создания новой директории
- -p - параметр mkdir, который позволяет создавать родительские директории при их отсутствии (рекурсивное создание目录)
- /mnt/common_volume/grafana/{grafana-config,grafana-data,prometheus-data} - путь к нескольким директориям, которые будут созданы одновременно:
  - `/mnt/common_volume/grafana/grafana-config`
  - `/mnt/common_volume/grafana/grafana-data`
  - `/mnt/common_volume/grafana/prometheus-data`

Эта команда создает три директории (`grafana-config`, `grafana-data`, `prometheus-data`) внутри пути `/mnt/common_volume/grafana/`, используя фигурные скобки для указания нескольких имен директорий. Все промежуточные каталоги также создаются автоматически, если они еще не существуют (рис. 9).

<div align="center">
   <img src="https://github.com/user-attachments/assets/0e7f3333-6d38-47bf-913a-0bb6672bedde" alt="" width="1000">
   <p>Рисунок 9 - Создание новых 3 директорий</p>
</div>

```bash
sudo chown -R $(id -u):$(id -g) {/mnt/common_volume/swarm/grafana/config,/mnt/common_volume/grafana}
```

- sudo - команда для выполнения операции с правами суперпользователя (администратора)
- chown - утилита для изменения владельца и группы файла или директории
- -R - параметр chown, указывающий на рекурсивное изменение прав для всех файлов и поддиректорий внутри указанной директории
- $(id -u) - команда, возвращающая UID (идентификатор пользователя) текущего пользователя
- $(id -g) - команда, возвращающая GID (идентификатор группы) основной группы текущего пользователя
- {/mnt/common_volume/swarm/grafana/config,/mnt/common_volume/grafana} - список директорий, для которых будут изменены владелец и группа:
  - `/mnt/common_volume/swarm/grafana/config`
  - `/mnt/common_volume/grafana`

Эта команда меняет владельца и группу указанных директорий (`/mnt/common_volume/swarm/grafana/config` и `/mnt/common_volume/grafana`) на текущего пользователя и его основную группу, причем изменения применяются рекурсивно ко всем файлам и поддиректориям внутри этих директорий (рис. 10).

<div align="center">
   <img src="https://github.com/user-attachments/assets/e72af7a6-696f-4e04-95d4-c3525a7c1912" alt="" width="1000">
   <p>Рисунок 10 - Группа директорий</p>
</div>

```bash
touch /mnt/common_volume/grafana/grafana-config/grafana.ini
```

- touch - команда для создания нового файла или обновления временной метки существующего файла
- /mnt/common_volume/grafana/grafana-config/grafana.ini - путь к файлу, который будет создан или обновлен

Эта команда создает новый пустой файл `grafana.ini` по указанному пути `/mnt/common_volume/grafana/grafana-config/`, если он еще не существует. Если файл уже существует, команда просто обновит его временную метку последнего доступа (рис. 11).

<div align="center">
   <img src="https://github.com/user-attachments/assets/2e8095c1-9986-48a4-b6bc-0f843eb1e13f" alt="" width="1000">
   <p>Рисунок 11 - Новый файл</p>
</div>

```bash
cp config/* /mnt/common_volume/swarm/grafana/config/
```

- cp - команда для копирования файлов и директорий
- config/* - путь к файлам, которые нужно скопировать (все файлы из директории `config`)
- /mnt/common_volume/swarm/grafana/config/ - целевая директория, куда будут скопированы файлы

Эта команда копирует все файлы из директории `config` в указанную директорию `/mnt/common_volume/swarm/grafana/config/`. Если в исходной директории есть поддиректории, они не будут скопированы, так как параметр `-r` (рекурсивное копирование) не используется (рис. 12).

<div align="center">
   <img src="https://github.com/user-attachments/assets/94ca5879-a177-4346-9867-c0d90b844f3e" alt="" width="1000">
   <p>Рисунок 12 - Копирование файлов</p>
</div>

```bash
mv grafana.yaml docker-compose.yaml
```

- mv - команда для переименования или перемещения файлов и директорий
- grafana.yaml - исходное имя файла
- docker-compose.yaml - новое имя файла

Эта команда переименовывает файл `grafana.yaml` в `docker-compose.yaml` в текущей директории. Если файлы находятся в разных директориях, команда также может использоваться для перемещения файла с изменением его имени (рис. 13).

<div align="center">
   <img src="https://github.com/user-attachments/assets/3983a4c2-6d3f-4ec6-8ca6-fed3c73e155b" alt="" width="1000">
   <p>Рисунок 13 - Новое имя файла</p>
</div>

```bash
sudo docker compose up -d
```

- sudo - команда для выполнения операции с правами суперпользователя (администратора)
- docker - утилита для управления контейнерами Docker
- compose - подкоманда Docker, используемая для работы с многосервисными приложениями, определенными в файле `docker-compose.yaml`
- up - параметр compose, который создает и запускает все сервисы, описанные в файле `docker-compose.yaml`
- -d - параметр, указывающий на запуск контейнеров в фоновом режиме (detached mode)

Эта команда запускает все сервисы, описанные в файле `docker-compose.yaml`, в фоновом режиме. Контейнеры будут созданы и начнут работу согласно заданным конфигурациям (рис. 14).

<div align="center">
   <img src="https://github.com/user-attachments/assets/d0d0b110-84a9-4679-9187-b468ae214036" alt="" width="1000">
   <p>Рисунок 14 - Поднятие Docker Compose</p>
</div>

## Задание 4

Поднял Docker Compose командой (рис. 1):

```bash
sudo docker compose up -d
```

<div align="center">
   <img src="https://github.com/user-attachments/assets/49542a9f-e439-454b-9962-1b5b429e02cb" alt="" width="1000">
   <p>Рисунок 1 - Docker Compose</p>
</div>

```bash
sudo docker compose stop
```

- sudo - команда для выполнения операции с правами суперпользователя (администратора)
- docker - утилита для управления контейнерами Docker
- compose - подкоманда Docker, используемая для работы с многосервисными приложениями, определенными в файле `docker-compose.yaml`
- stop - параметр compose, который останавливает все запущенные контейнеры, описанные в файле `docker-compose.yaml`, без их удаления

Эта команда останавливает все активные контейнеры, связанные с текущим файлом `docker-compose.yaml`, но не удаляет их. Остановленные контейнеры можно снова запустить с помощью команды `docker compose start` (рис. 2).

<div align="center">
   <img src="![изображение](https://github.com/user-attachments/assets/7a539aa8-f3e2-4714-8c30-ca542c12233d)
" alt="" width="1000">
   <p>Рисунок 2 - Остановка через stop</p>
</div>

```bash
sudo docker compose down
```

- sudo - команда для выполнения операции с правами суперпользователя (администратора)
- docker - утилита для управления контейнерами Docker
- compose - подкоманда Docker, используемая для работы с многосервисными приложениями, определенными в файле `docker-compose.yaml`
- down - параметр compose, который останавливает и удаляет все контейнеры, сети, тома и образы, созданные для данного состава (composition)

Эта команда останавливает и удаляет все сервисы, контейнеры, сети и тома, связанные с текущим файлом `docker-compose.yaml`, очищая окружение после работы (рис. 3).

<div align="center">
   <img src="https://github.com/user-attachments/assets/7d2521cb-1ec0-41b1-bf0a-b6d672e5e6c8" alt="" width="1000">
   <p>Рисунок 3 - Остановка через down</p>
</div>

```bash
sudo docker compose ps
```

-sudo - команда для выполнения операции с правами суперпользователя (администратора)
-docker - утилита для управления контейнерами Docker
-compose - подкоманда Docker, используемая для работы с многосервисными приложениями, определенными в файле `docker-compose.yaml`
- ps - параметр compose, который показывает статус запущенных контейнеров, описанных в файле `docker-compose.yaml`

Эта команда выводит список всех контейнеров, связанных с текущим файлом `docker-compose.yaml`, вместе с их состоянием (запущены/остановлены), идентификаторами, портами и другими важными данными. Она помогает проверить, какие сервисы активны в данный момент (рис. 4).

<div align="center">
   <img src="https://github.com/user-attachments/assets/a9b06062-47c8-4fdc-b137-d0dcdebbde2e" alt="" width="1000">
   <p>Рисунок 4 - Список контейнеров</p>
</div>

