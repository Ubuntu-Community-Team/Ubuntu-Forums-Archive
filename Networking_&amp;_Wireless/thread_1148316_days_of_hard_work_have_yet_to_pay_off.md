---
title: "days of hard work have yet to pay off"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by tophat2445 on 2009-05-04
Okej, heres my problem. 

Ubuntu WILL NOT connect to my wireless connection.  It recognizes my wireless card, it recognizes my router...but when I try to connect....NOTHING!!! 

I'm using Ubuntu 9.04(flash drive boot) on an HP Pavilion dv6000.  My router is a NETGEAR WPN824v3.

Please please help

Kenny

---

### Post by x22 on 2009-05-04
what I do is run this script "wireless" from "/etc/rc.local" 

ifconfig wlan0 up
iwconfig wlan0 essid chris
iwconfig wlan0 channel 11
iwconfig wlan0 mode managed
iwconfig wlan0 key 1234567890
iwconfig wlan0 key open
dhclient wlan0

WEP encryption. Change to suit your local setup

---

