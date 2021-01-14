# Kafka + CLI

## Creating a topic
docker exec -it kafka_kafka-setup_1 kafka-topics --zookeeper zookeeper:2181 --create --topic vini-topic --partitions 3 --replication-factor 1

## Listing all topics
docker exec -it kafka_kafka-setup_1 kafka-topics --zookeeper zookeeper:2181 --list

## Details of a specif topic
docker exec -it kafka_kafka-setup_1 kafka-topics --zookeeper zookeeper:2181 --describe --topic vini-topic

## Producer
docker exec -it kafka_kafka-setup_1 kafka-console-producer --bootstrap-server kafka-setup:9091 --topic vini-topic

## Consumer
docker exec -it kafka_kafka-setup_1 kafka-console-consumer --bootstrap-server kafka-setup:9091 --topic vini-topic

### Consumers group
docker exec -it kafka_kafka-setup_1 kafka-console-consumer --bootstrap-server kafka-setup:9091 --topic vini-topic --group my-first-application-group

### List consumer groups
docker exec -it kafka_kafka-setup_1 kafka-consumer-groups --bootstrap-server kafka-setup:9091 --list

### Details of a consumer group
docker exec -it kafka_kafka-setup_1 kafka-consumer-groups --bootstrap-server kafka-setup:9091 --describe --group my-first-application-group

### Resetting Offsets
docker exec -it kafka_kafka-setup_1 kafka-consumer-groups --bootstrap-server kafka-setup:9091 --group my-first-application-group --reset-offsets --to-earliest --execute --topic vini-topic