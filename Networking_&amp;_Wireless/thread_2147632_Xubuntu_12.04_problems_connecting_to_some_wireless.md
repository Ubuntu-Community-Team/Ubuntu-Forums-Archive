---
title: "Xubuntu 12.04 problems connecting to *some* wireless networks"
date: 2013-05-22
forum: Networking &amp; Wireless
---

### Post by chellrose on 2013-05-22
I'm running Xubuntu 12.04 (and using whatever the default 'net connection software is).  I was able to connect to wireless, no problem, out-of-the-box.  I've successfully connected to my own home network (WPA secured) as well as the unsecured network at my local Starbucks.  However, I can't connect to the unsecured wifi network at the library.  The network connection indicator is stuck in "connecting..." mode.

I'm currently connected to the aforementioned network via WinXP, so I'm sure it isn't a problem with the network itself.

---

### Post by Hadaka on 2013-05-22
Hi, if you are currently still at the library
please post the output of..
```
nm-tool
iwlist wlan0 scan

```
*Note your wireless may be eth1..wlan1 enter correct
data for scan
thanks.

---

### Post by Mark Phelps on 2013-05-22
Suggest you try installing WiFi Radar and see if it does a better job of connecting.

---

### Post by chellrose on 2013-05-23
It finally connected, after I let it sit there for about 10-15 minutes.  That seems strange, because I can connect to other networks in under a minute.  But at least it's connected.

I'll check out Wifi Radar if I have any more troubles.  Thanks for the tip.

---

