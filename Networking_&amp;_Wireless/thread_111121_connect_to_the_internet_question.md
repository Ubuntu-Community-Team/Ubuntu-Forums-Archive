---
title: "connect to the internet question"
date: 2006-01-01
forum: Networking &amp; Wireless
---

### Post by paul555 on 2006-01-01
Hi all and happy new year i have a microcom external modem and i want to connect to the internet with it.My pc is also connected to a lan in my home throw a switch.I setup wvdial which recognizes my modem but i can't connect.Here is my wvdial.conf :
```
[Dialer Defaults]
Modem = /dev/ttyS0
ISDN = off
Modem Type = Analog Modem
Baud = 115200
Init = ATX3
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Phone = &#967;&#967;&#967;&#967;&#967;&#967;&#967;&#967;&#967;&#967;&#967;
Dial Attempts = 2
Dial Command = ATM0L0DT
Ask Password = off
Password = &#967;&#967;&#967;&#967;&#967;&#967;&#967;&#967;&#967;&#967;
Username = &#967;&#967;&#967;&#967;&#967;&#967;&#967;&#967;&#967;&#967;
Auto Reconnect = off
Abort on Busy = off
Carrier Check = on
Check Def Route = on
Abort on No Dialtone = on
Stupid Mode = off
Idle Seconds = 0
Auto DNS = on
```
Is there a gui program to help me connect like kppp?Thanks for your time

---

