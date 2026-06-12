---
title: "Only able to connect to Google in 9.04"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by etomar on 2010-08-13
I installed Ubuntu 9.04 on my laptop (need to upgrade drivers, 10.4 installation won't even start with SiS Mirage 3 graphics), and everything works fine other than a messed up resolution attributed to the drivers. However, when connecting to the internet via my ethernet connection, I can only go to Google (search, gmail, etc.). Any other site only displays "Waiting for..." and won't connect. A very weird problem, and the only solution I found said to [change MTU to 1400]("https://answers.launchpad.net/ubuntu/+question/51214"), but I don't know what that means. :confused: Any help?

Thanks!

---

### Post by Kerubu on 2010-08-13
Post the results of the following command :

ifconfig

---

### Post by etomar on 2010-08-13
OK, here it is.

```
eth0      Link encap:Ethernet  HWaddr 00:21:85:e2:2d:60  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


```

---

### Post by etomar on 2010-08-13
Well, I Googled how to change MTU and changed it to 1400, and that seems to have fixed the problem. Still weird, though.

---

