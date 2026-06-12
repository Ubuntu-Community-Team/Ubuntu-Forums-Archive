---
title: "Intermittent Connections to Internet"
date: 2013-01-19
forum: Networking &amp; Wireless
---

### Post by wjdearborn on 2013-01-19
On Ubuntu 12.10 64 bit running on a AMD Athlon II X2 processor on a wired connection to the internet via Dlink  Dir-857 and a Cable Modem both Firefox and Chrome cannot load some websites at all (appears to be those who transfer from straight http to https formats) and most others they never finish loading (i.e. symbol by the name in the tab on Firefox keeps spinning). This was not a problem on this system prior to upgrading from 12.04 LTS. 

I have tested the network with Wireless with the same router and modem connection and there are no problems with our Blackberry, a Android/Chrome combination, Windows/Internet Explorer, Ubuntu 12.04/Firefox and Chrome - all of these combinations work fine. I have also tested with a second wired machine running 12.04 and that one works fine. Swapping out the cable between the machine and router does not fix the situation. Since both Chrome and Firefox are effected I assume their internal preference settings are not at fault. Hence the assumption that the problem is with 12.10.

Somehow my network connection on the 12.10 machine is confused. The following is the output from ifconfig:

 eth0      Link encap:Ethernet  HWaddr 50:e5:49:6c:eb:9a  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::52e5:49ff:fe6c:eb9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2767 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2896 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1136401 (1.1 MB)  TX bytes:707332 (707.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:648 errors:0 dropped:0 overruns:0 frame:0
          TX packets:648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:73064 (73.0 KB)  TX bytes:73064 (73.0 KB)

Any help greatly appreciated...

Bill Dearborn

---

