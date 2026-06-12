---
title: "I can't connect to Internet through my router TP-LINK WR741ND"
date: 2012-09-06
forum: Networking &amp; Wireless
---

### Post by eflix1 on 2012-09-06
Hi!. This week I started to have a conectivity problem on my linux/windows computer. The router is new and was working properly for a week. The windows part connects correctly to the internet, while the linux OS (lubuntu 11.04) can't. This PC is connected to a router, which is connected to the modem (Huawei ZXDSL 831). With this setup I can't access the internet. At this point Ifconfig command says my computer has the ip 192.168.1.3 which is strange because my router is setup to give addresses from 192.168.0.100 on. The only workaround I know for this problem is to connect the PC directly to the modem. Once I have internet signal on the pc, I plug it back to the router, connect the router to the modem, and still have internet connection. Then I check ifconfig and it says my IP is 192.168.0.100. 
Right now I cant do that workaround anymore, it doesn't connect. 
This is the output of ifconfig:
```
eth0      Link encap:Ethernet  HWaddr f4:6d:04:ef:e2:79  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f66d:4ff:feef:e279/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1392 (1.3 KB)  TX bytes:11503 (11.5 KB)
          Interrupt:43 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:241 errors:0 dropped:0 overruns:0 frame:0
          TX packets:241 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17130 (17.1 KB)  TX bytes:17130 (17.1 KB) 
```
I reseted the router once but still have this problem. What can I do to solve this problem?

---

### Post by merlinus on 2012-09-06
You might try using a static IP address.

---

### Post by eflix1 on 2012-09-07
I did just that, and it worked. Problem solved. Thanks merlinus!.

---

### Post by eflix1 on 2012-09-07
> **merlinus said:**
> You might try using a static IP address.

I did that through nm-applet and now it works. Thank you merlinus!. Problem solved.

---

### Post by merlinus on 2012-09-07
Glad it worked for you!

---

