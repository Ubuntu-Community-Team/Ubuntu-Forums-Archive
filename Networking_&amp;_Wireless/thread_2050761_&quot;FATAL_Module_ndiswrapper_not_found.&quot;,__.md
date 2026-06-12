---
title: "&quot;FATAL: Module ndiswrapper not found.&quot;,  on 12.4 Pangolin"
date: 2012-08-31
forum: Networking &amp; Wireless
---

### Post by clausrei on 2012-08-31
Hi,

I have not clue of Ndiswrapper. It is the first time I use it. I just installed a Windows driver (.inf file) to get an Siemens Gigaset USB Adapter 54 to work. I used the driver on the CD-ROM.


When I make a modeprobe, I get this message :
```

claus@rosi:/media/Gigaset/Installation/Gigaset USB Adapter 54/Driver$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.


```With lsusb I have th following message: 
```
 
claus@rosi:/media/Gigaset/Installation/Gigaset USB Adapter 54/Driver$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 083a:4521 Accton Technology Corp. Siemens S30863-S1016-R107-2 802.11g Wireless Adapter [Intersil ISL3887]
Bus 003 Device 002: ID 080d:0102 Teco Image Systems Co., Ltd Hercules Scan@home 48

```How can I check the driver is working correctly? 
**This is a Precise Pangolin new installation  from CD-ROM not an upgrate.  **But if I have to change some directory I have no clue how and where?

Thanks for your help.

Claus

---

### Post by clausrei on 2012-09-01
Solved the solution was here:

[http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found](http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found)

---

