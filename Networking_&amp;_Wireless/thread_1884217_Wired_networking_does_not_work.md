---
title: "Wired networking does not work"
date: 2011-11-20
forum: Networking &amp; Wireless
---

### Post by turbo47 on 2011-11-20
Currently on a laptop. The wireless connection works beautifully but when I plug in an ethernet cable, it just repeatedly gives me the message that I can disconnect anifd offline. I have tried plugging it in with wifi both on and off to no avail. What should I do?

Results of ifconfig (wifi on, ethernet unplugged)

eth0      Link encap:Ethernet  HWaddr 54:42:49:5e:34:9d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7564 (7.5 KB)  TX bytes:18483 (18.4 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:158 (158.0 B)  TX bytes:158 (158.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:23:14:a4:d6:a4  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:14ff:fea4:d6a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:84662 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34934 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:94215835 (94.2 MB)  TX bytes:3422539 (3.4 MB)

---

