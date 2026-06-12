---
title: "Ubuntu 10.04 - how to use PPTP after setup"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by markwen on 2010-10-15
Hi Everyone,

Trying to connect to my office as a PPTP client, I have setup my PPTP connection in Ubuntu 10.04, and the connection is active, as I can see from the top bar, and the output of ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:18:8b:b7:a3:ef  
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
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:580 (580.0 B)  TX bytes:580 (580.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.0.166  P-t-P:192.168.0.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1400  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:108 (108.0 B)  TX bytes:96 (96.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:7a:96:e5  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe7a:96e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8525 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5799296 (5.7 MB)  TX bytes:1408867 (1.4 MB)
```Now I want to access the folder named ABC on the remote PC with IP address of 192.168.0.12, with username USER1 and password PASS1. Could anyone tell me how to do that?

Thanks a lot.

---

### Post by markwen on 2010-10-16
Anybody give me a hand?

Thanks.

---

### Post by markwen on 2010-10-20
Still expecting some help.

---

