---
title: "Asus WL-520GC Router"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by Rymer on 2009-09-13
Hi all!
I've installed ubuntu on my laptop and now i'm trying to set connection with internet. 
The situation is so: a cable is inserted to router and router is connected with P&#1057; (with winXP on it), using cable too. And laptop "gets" internet wireless. When Vista was installed on my laptop, everything was simple - just insert a CD, and setup.exe will install all settings. 
But now i don't know where to srart((( I've tried to google something on that point, but did not find anything that can help( ](*,) 
Is there any manuals/utilities/drivers/or_i_don't_know_what_can_it_be that can help in that question? :roll:

PS: sorry for my English, it's not my native language.

UPD:
[http://192.168.1.1/](http://192.168.1.1/) shows connections failture
ping  192.168.1.1 shows network is unreachable, but localhost ping is ok.
Here is ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:23:54:13:67:e5  
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
         Interrupt:247 Base address:0xc000 

lo        Link encap:Local Loopback  
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:294 errors:0 dropped:0 overruns:0 frame:0
         TX packets:294 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0 
         RX bytes:23204 (23.2 KB)  TX bytes:23204 (23.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:5d:0e:fa:ea  
         inet6 addr: fe80::221:5dff:fe0e:faea/64 Scope:Link
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-5D-0E-FA-EA-61-65-00-00-00-00-00-00-00-00  
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

