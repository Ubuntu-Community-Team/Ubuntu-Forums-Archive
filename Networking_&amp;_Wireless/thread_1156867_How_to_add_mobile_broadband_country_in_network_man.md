---
title: "How to add mobile broadband country in network manager?"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by felixdzerzhinsky on 2009-05-12
I am based in Cambodia. My ISP is Star-Cell. 

How do I add  a mobile broadband country in network manager? Cambodia is not listed. [www.star-cell.net/](www.star-cell.net/)

My /etc/wvdial.conf that works is:

> [Dialer Defaults] 

Modem = /dev/ttyACM0

Baud = 230400 

Init1 = ATZ 

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 

ISDN = 0 

Modem Type = Analog Modem 

Phone = *99***1# 

Username = "aa" 

Password = "aa" 

Stupid Mode = 1 


Is there a way to get this to work?

---

