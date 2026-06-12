---
title: "Can't connect to wireless network"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by Harry617 on 2010-12-19
Hi there, I'm about to install Ubuntu 10.10, but I can't connect to my wireless network. 
I can see it under available networks, but when I try to connect to it (I'm using WEP, I live at the end of a dead end street and none of my neighbours are smart enough to crack it)
it dosen't work and keeps asking me for the key over and over again.
I know I have the right key though.

---

### Post by Harry617 on 2010-12-19
Here are the results of my ifconfig

>                                   ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:78:18:05:c2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1776 (1.7 KB)  TX bytes:1776 (1.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:e0:4c:73:2f:c5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


---

