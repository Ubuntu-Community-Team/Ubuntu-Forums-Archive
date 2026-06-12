---
title: "Intermittent WiFi IP failure"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by alco75 on 2010-11-27
Sometimes, maybe every third time I start up Ubuntu, I don't get an IP address and have to reboot my router to get one. It doesn't happen to my iPhone or my wife's XP machine.

ifconfig shows:

```
misiek@mike-pc:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:50:8d:9f:b8:61  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:372 errors:0 dropped:0 overruns:0 frame:0
          TX packets:372 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30163 (30.1 KB)  TX bytes:30163 (30.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:17:a7:00  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe17:a700/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4972 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7955 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2325314 (2.3 MB)  TX bytes:2799548 (2.7 MB)

```

Which is okay now, but sometimes **inet addr** entry under wlan0 is blank. Any ideas what could be causing that?

I'm on 10.04 LTS and the router is a BT Voyager 2100.

---

