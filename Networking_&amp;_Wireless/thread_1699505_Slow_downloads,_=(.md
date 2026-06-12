---
title: "Slow downloads, =("
date: 2011-03-03
forum: Networking &amp; Wireless
---

### Post by natrualwater on 2011-03-03
Hi guys, I'm getting very very slow downloads with Ubuntu, i just switched over to linux about 3 hours ago.

Hopefully you guys can help, anyway here is the "ifconfig"

eth0      Link encap:Ethernet  HWaddr 6c:f0:49:73:2b:a2  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6ef0:49ff:fe73:2ba2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:858187 errors:0 dropped:0 overruns:0 frame:0
          TX packets:548464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1217279865 (1.2 GB)  TX bytes:52814676 (52.8 MB)
          Interrupt:49 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1540 (1.5 KB)  TX bytes:1540 (1.5 KB)

---

### Post by byStanderone on 2011-03-03
...try disabling ipv6 for a moment, some providers does not support it yet.

---

