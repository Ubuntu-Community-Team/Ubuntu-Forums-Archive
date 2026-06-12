---
title: "Problem With Huawei E3131"
date: 2012-11-10
forum: Networking &amp; Wireless
---

### Post by legio314 on 2012-11-10
Hello Guys,i just started using ubuntu 12.10 on an old acer TravelMate 4200.

My problem lies with my recent acquisition of a huawei hsdpa usb modem.

The included (with ubuntu) network manager does not recognise the device.

Currently I connect using wvdial,here's the config file i use:


```

[Dialer hsdpa]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Modem Type = Analog Modem
 Phone = *99#
ISDN = 0
 Password = web
New PPPD = yes
 Username = web
Modem = /dev/ttyUSB_utps_modem
Baud = 9600
Stupid Mode = 1
Dial Command = ATDT

```Thanks In Advance!
:D

---

