---
title: "can't connect to linksys wrt54ds router"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by mitc1425 on 2009-02-26
I have been searching all over the threads for answers but to no avail...I have a desktop connected by wire to my linksys router and cannot connect to it. I have tried using 192.168.1.1 to access it and that does not work...Since my ISP is DSL, I have set up my router to automatically connect through PPpOE...I used the sudo pppoeconf command and it found eth0...I selected yes...and got a not connected message...ifconfig gave me 
eth0     Link encap:Ethernet   HWaddr 0007:e9:b1:9a:52
         UP BROADCAST MULTICAST   MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)   TX bytes:0 (0.0 B)

lo       Link encap:Local Loopback
         inet addr:127.0.0.1  Mask 255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:25190 errors:0 dropped:0 overruns:0 frame:0
         TX packets:25190 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:1276172 (1.2 MB)  TX bytes:1276172 (1.2 MB)

please help...I have no problems accessing my router with my windows boxes but since i am completely new to linux I have no diagnostic skills as of yet...thanks in advance

---

### Post by stardash on 2009-02-26
> **mitc1425 said:**
> I have been searching all over the threads for answers but to no avail...I have a desktop connected by wire to my linksys router and cannot connect to it. I have tried using 192.168.1.1 to access it and that does not work...Since my ISP is DSL, I have set up my router to automatically connect through PPpOE...I used the sudo pppoeconf command and it found eth0...I selected yes...and got a not connected message...ifconfig gave me 
eth0     Link encap:Ethernet   HWaddr 0007:e9:b1:9a:52
         UP BROADCAST MULTICAST   MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)   TX bytes:0 (0.0 B)

lo       Link encap:Local Loopback
         inet addr:127.0.0.1  Mask 255.0.0.0
         inet6 addr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:25190 errors:0 dropped:0 overruns:0 frame:0
         TX packets:25190 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:1276172 (1.2 MB)  TX bytes:1276172 (1.2 MB)

please help...I have no problems accessing my router with my windows boxes but since i am completely new to linux I have no diagnostic skills as of yet...thanks in advance


This thread goes over your exact problem. He has gotten a lot closer to a solution and started right were you are now

[http://ubuntuforums.org/showthread.php?t=1081318](http://ubuntuforums.org/showthread.php?t=1081318)

---

### Post by superprash2003 on 2009-02-26
in your terminal type **sudo dhclient eth0** and then post output of ifconfig again.. your eth0 isnt getting an ip..

---

### Post by mitc1425 on 2009-02-26
hammer@the-bratz:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 5787
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:07:e9:b1:9a:52
Sending on   LPF/eth0/00:07:e9:b1:9a:52
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.100 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.100 from 192.168.1.1
bound to 192.168.1.100 -- renewal in 37739 seconds.
hammer@the-bratz:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:e9:b1:9a:52  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:feb1:9a52/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1609 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1807000 (1.7 MB)  TX bytes:123427 (120.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1342 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1342 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:67100 (65.5 KB)  TX bytes:67100 (65.5 KB)

---

### Post by superprash2003 on 2009-02-27
now your eth0 has 192.168.1.100 as ip ( thats good) isnt it working now?

---

