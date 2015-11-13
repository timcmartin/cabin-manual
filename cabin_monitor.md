# Cabin Monitor

Temperature and power monitoring system, powered by a Raspberry Pi and an APC BE550G  UPS system.

URL: [http://cabin-monitor.herokuapp.com](http://cabin-monitor.herokuapp.com/)

All details can be found in [this repo](https://bitbucket.org/timcmartin/cabin-monitor)

Repo is linked to Heroku deployments via Codeship.

## Raspberry Pi

Currently running Raspbian and hardwired via ethernet to the router.  It is running a temperature sensor via GPIO and monitors the UPS via USB.

## UPS

Currently an APC BE550G and using the APCUPSD software on the Raspberry Pi.  There are onbattery and offbattery scripts that send emails when the power goes out and returns.

## Temperature

An hourly cron job on the Raspberry Pi triggers a Python script to run and obtain the temperature from the sensor. This script then hits a RESTful API that records the temperature.  The API then hits the [Openweathermap API](http://openweathermap.org/) to record the current external temperatures of Olds, Bowden and Innisfail.

* Should the internal temperature of the cabin hit 5 C or below, a cold alert will be emailed.

* Should the internal temperature hit 0 C or lower, a freeze alert will be emailed.

* Should the internal temperature of the cabin reach 30 C or higher, a heat alert will be emailed.
