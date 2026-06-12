---
title: "No IPv6 Route"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by Bender59 on 2010-08-11
I'm trying to use Scapy for in a program I'm making, but whenever I run 'from scapy.all import *', I get this error:```
WARNING: No route found for IPv6 destination :: (no default route?)
```Does anyone have an idea what this means, or how I can fix it?

This is the output of ifconfig:```
eth0      Link encap:Ethernet  HWaddr 00:19:d1:3d:34:0e  
          inet addr:192.168.0.192  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe3d:340e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:967039 errors:0 dropped:0 overruns:0 frame:0
          TX packets:668215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:336988743 (336.9 MB)  TX bytes:82198168 (82.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1521747 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1521747 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:263595755 (263.5 MB)  TX bytes:263595755 (263.5 MB)
```

---

