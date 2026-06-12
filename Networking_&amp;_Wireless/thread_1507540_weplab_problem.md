---
title: "weplab problem"
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by The Low End Theory on 2010-06-11
ok so i use this script

```
#!/bin/bash

sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
sudo weplab -c test.pcap
```to capture trafic, however it gives me an error saying > pcap_open_live(): wlan0: That device is not uphowever it if i add
```
sudo ifconfig wlan0 up
```before the last line, it takes it out of monitor mode. does anyone know what to do?

edit: im not entirely sure that adding that extra line does anything at all, since i just figured that it would would stop the device from being "down" does anyone know if this actually does that?

---

