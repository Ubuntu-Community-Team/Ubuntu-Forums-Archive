---
title: "Wired connection toTime Machine will not connect to Internet"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by debeyt on 2008-12-29
I have a 1TB Apple Time Machine connected by wirelessly to a MacBook Pro, a MacBook and a PowerBook G4. All connected without any problem. At times I have hooked these machines up by wire and that works fine. 

I also have a Ubuntu desktop machine connected by wire. This used to work no problem. Then I upgraded to Ubuntu 10.10! Although I can ping [www.google.ca](www.google.ca), and various other sites on the web, I can not connect by browser. FireFox keeps attempting to connect for hours on end. When I try a traceroute, it will trace all the way to the desired site which will not reply.

tom@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:5b:50:4b:4d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xd800 

eth1      Link encap:Ethernet  HWaddr 00:a0:cc:34:a7:9d  
          inet addr:10.0.1.148  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:ccff:fe34:a79d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12524 errors:5725 dropped:0 overruns:0 frame:5889
          TX packets:124296 errors:1 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:1258470 (1.2 MB)  TX bytes:12277258 (12.2 MB)
          Interrupt:19 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:539 errors:0 dropped:0 overruns:0 frame:0
          TX packets:539 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:36200 (36.2 KB)  TX bytes:36200 (36.2 KB)

Any ideas any one?

---

