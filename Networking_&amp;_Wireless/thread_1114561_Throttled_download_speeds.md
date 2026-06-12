---
title: "Throttled download speeds"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by MrDead on 2009-04-02
I recently installed Ubuntu 9.04 on my new desktop and it actually connected to my network very easily compared to 8.10 and 8.04, but my problem is that the download speed is incredibly low. According to Speedtest.net my DL speed is 0.24 mbps while my upload is 1.76 mbps ?! Now, when I had XP installed I was getting speeds like 9.86 Mbps (btw I have verizon FiOS) and now I rarely get DL speeds over 100 kbps. On another computer on my network I'm getting speeds like 1.2 mbps on regular downloads, and it's incredibly annoying as it takes hours to download anything or update my system. I hope this has something to do with some port not being opened or something, but from my experience it's never that simple. If anyone has any suggestions I will be very happy. By the way I am connecting through a Ralink USB card and the rt2870 driver.

EDIT: Tangential problem solved

---

### Post by superprash2003 on 2009-04-03
problem solved?? if not post output of ifconfig from the terminal

---

### Post by MrDead on 2009-04-03
Here is my ifconfig output:

eth0      Link encap:Ethernet  HWaddr 00:24:8c:37:81:36  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1260 (1.2 KB)  TX bytes:1260 (1.2 KB)

ra0       Link encap:Ethernet  HWaddr 00:18:e7:4a:48:b6  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:e7ff:fe4a:48b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:143649 errors:144 dropped:0 overruns:0 frame:0
          TX packets:86950 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30420471 (30.4 MB)  TX bytes:6677874 (6.6 MB)

---

### Post by MrDead on 2009-04-08
Bump, anybody? And yes, I still have very slow downloads.

---

