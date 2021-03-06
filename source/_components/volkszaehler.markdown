---
layout: page
title: "Volkszaehler"
description: "Instructions on how to integrate Volkszaehler sensors into Home Assistant."
date: 2018-08-25 08:00
sidebar: true
comments: false
sharing: true
footer: true
logo: volkszaehler.png
ha_category: System Monitor
ha_iot_class: Local Polling
ha_release: 0.78
redirect_from:
 - /components/sensor.volkszaehler/
---

The `volkszaehler` sensor platform is consuming the system information provided by the [Volkszaehler](https://wiki.volkszaehler.org/) API.

## {% linkable_title Configuration %}

To enable the Volkszaehler sensor, add the following lines to your `configuration.yaml`:

```yaml
# Example configuration.yaml entry
sensor:
  - platform: volkszaehler
    uuid: DEVICE_UUID
```

{% configuration %}
uuid:
  description: The UUID of the device to track.
  required: true
  type: string
host:
  description: The IP address of the host where Volkszaehler is running.
  required: false
  type: string
  default: localhost
port:
  description: The port where Volkszaehler is listening.
  required: false
  type: integer
  default: 80
name:
  description: The prefix for the sensors.
  required: false
  type: string
  default: Volkszaehler
monitored_conditions:
  description: Entries to monitor.
  required: false
  type: map
  default: average
  keys:
    average:
      description: The average power.
    consumption:
      description: The power consumption.
    max:
      description: The maximum power.
    min:
      description: The minimum power.
{% endconfiguration %}

## {% linkable_title Full examples %}

```yaml
# Example configuration.yaml entry
sensor:
  - platform: volkszaehler
    host: demo.volkszaehler.org
    uuid: '57acbef0-88a9-11e4-934f-6b0f9ecd95a8'
    monitored_conditions:
      - average
      - consumption
      - min
      - max
```
