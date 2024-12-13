# Кластер Kafka + экспортеры метрик

**Цель: поднять простейший кластер Кафки из нескольких брокеров, прикрутить экспортеры метрик и посмотреть, что они собственно экспортируют.**

В качестве экспортеров взял два экспортера, упоминания которых попались мне, когда копал тему.

https://github.com/danielqsj/kafka_exporter

https://www.entechlog.com/blog/kafka/monitoring-kafka-consumer-lag/

## Ссылки

Проверяем работу экспортеров прямо через браузер:
* http://localhost:9318/metrics
* http://localhost:9328/metrics

Консоли UI:
* Kafka UI: http://localhost:8180
* Prometheus: http://localhost:9190
* Состояние подключений Prometheus к экспортерам: http://localhost:9190/targets
* Grafana: http://localhost:3100

## Стартовые сообщения в топиках

См. `docker-compose: kafka-init-topics` - создание топиков, отправка в них партии сообщений

## Настройки версий и портов

Все настройки в файле `.env`

## Дополнительные ссылки

Kafka Listeners - Explained: https://rmoff.net/2018/08/02/kafka-listeners-explained/

Пример использования kcat (https://github.com/edenhill/kcat)
```shell
docker run -it --network=host edenhill/kcat:1.7.1 -b localhost:9092 -L
```
Консольные команды Kafka CLI: https://docs.confluent.io/kafka/operations-tools/kafka-tools.html#kafka-console-consumer-sh

Настройка сетевого взаимодействия:
* Networking in Compose https://docs.docker.com/compose/how-tos/networking/
* Networks top-level elements https://docs.docker.com/reference/compose-file/networks/
* Network drivers https://docs.docker.com/engine/network/drivers/
* Communication between multiple docker-compose projects https://stackoverflow.com/questions/38088279/communication-between-multiple-docker-compose-projects
* https://www.baeldung.com/ops/docker-compose-communication
