---
title: "UMTS/3g dial with gnome ppp or using Huawei E220/E270 wvdial.conf files"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by Sylslay on 2009-01-01
This is list for wvdial.conf, It startup with Gnome and working fine with O2 Ireland


[Dialer Defaults]
Phone = *99#
Username = gprs
Password = gprs
New PPPD = yes
Dial Command = ATDT
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
Baud = 460800
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init5 = AT+CGDCONT=1,"IP","open.internet";
Stupid Mode = 1
Auto DNS = 1
 
//End BTW I pleaced modem in ceramic bowl and have 3,4 time faster speed
checed on czeski.dsl. Ceramic cup working good eithed. Some one know it's cancel bad fq noise or ampilfire signal

---

