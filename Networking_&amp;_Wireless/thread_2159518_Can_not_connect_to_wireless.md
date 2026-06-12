---
title: "Can not connect to wireless"
date: 2013-07-03
forum: Networking &amp; Wireless
---

### Post by brick2 on 2013-07-03
Hello

I just managed to set up the wirless connection, it took a while but now i can see all the connections around me. However I can not connect to any of them including my own. Any ideas as to what might be the problem. I read on a few posts that ndiswraper adjustmes are needed but for that they sugest blacklisting broadcome drivers, I really had a hard time making them work so I dont feel like messing around with them. Please if you could shed some light on this matter.

Dell laptop

Device: 08:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:26:b9:ed:cf:3a  
          inet addr:77.77.230.35  Bcast:77.77.231.255  Mask:255.255.252.0
          inet6 addr: fe80::226:b9ff:feed:cf3a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49032 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22360 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56526548 (56.5 MB)  TX bytes:1835969 (1.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:418 errors:0 dropped:0 overruns:0 frame:0
          TX packets:418 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77017 (77.0 KB)  TX bytes:77017 (77.0 KB)

wlan0     Link encap:Ethernet  HWaddr 78:e4:00:b3:88:3d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by chili555 on 2013-07-03
With the ethernet connected, please open a terminal and do:```
sudo apt-get install bcmwl-kernel-source
sudo modprobe -r b43
sudo modprobe wl
```Is it working better now?

---

### Post by brick2 on 2013-07-03
It works, o man I m infinetly greatfull, I wish there was something I could do for you all. 

See if this makes you smile.

What is motocyclist without a helm?
An organ donor.

---

