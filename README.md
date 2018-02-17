# Gaia Platform on Docker images (GAIA PROJECT)

## STACK

### [Influxdata Full TICK Stack](https://github.com/influxdata)

* InfluxDB
* Telegraf
* Chronograf
* Kapacitor

### MQTT Broker

* [mosquitto](https://github.com/eclipse/mosquitto)


## Usage

```
$ git clone https://github.com/smorcuend/gaia-docker.git
$ cd gaia-docker && docker-compose up -d
```
### Check that InfluxDB works:

Run this curl command, if no errors occur InfluxDB is running:

    curl http://localhost:8086/ping


#### The `influx` client

Use the built-in influx cli service:

    docker-compose run influxdb-cli

### Check that Telegraf works

By default, the Telegraf creates a `telegraf` database.
Check that InfluxDB has such a database in addition to the `_internal` database.

    docker-compose run influxdb-cli
    > show databases

### Check that Chronograf works

Access the Chronograf inteface, [http://localhost:8888](http://localhost:8888)

### Check Kapacitor works

First, run this curl command, if no errors occur Kapacitor is running:

    curl http://localhost:9092/kapacitor/v1/ping


Use the built-in kapacitor cli service:

    docker-compose run kapacitor-cli
    $ kapacitor list tasks

Confirm Kapacitor is subscribed to all databases in InfluxDB

    docker-compose run influxdb-cli
    > show subscriptions

## Supported Docker versions

This image is officially supported on Docker version 1.10.1 or newer.

## License
MIT
