---
title: "Connect to secure network via script"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by buster2209 on 2010-11-02
Does anyone have a way of connecting to a secure network via a bash script?

E.g;
```
#! /bin/bash

sudo su
iwconfig wlan0 stop
iwconfig wlan0 essid NETWORK_NAME
iwconfig wlan0 key NETWORK_KEY
iwconfig wlan0 start
```

---

### Post by buster2209 on 2010-11-03
bump bump bump!

---

### Post by buster2209 on 2010-11-03
If not via a script, is it possible via Terminal commands?

---

