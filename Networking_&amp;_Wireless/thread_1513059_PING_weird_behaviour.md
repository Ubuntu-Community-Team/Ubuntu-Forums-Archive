---
title: "PING weird behaviour"
date: 2010-06-18
forum: Networking &amp; Wireless
---

### Post by spandey on 2010-06-18
Hi,
I have Ubuntu LUCID. When I try PING -s option, it truncates anything other than 48.Which is strange? What can be the reason?

Here is my IFCONFIG output

spandey@spandey-desktop:~$ ifconfig
eth0     Link encap:Ethernet  HWaddr[COLOR=Black] 00:22:b0:e5:91:77  [/COLOR]
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29773 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28659856 (28.6 MB)  TX bytes:4767652 (4.7 MB)
          Interrupt:21 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 B)  TX bytes:300 (300.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:117.197.247.52  P-t-P:117.197.240.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:29386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:27976473 (27.9 MB)  TX bytes:4224207 (4.2 MB)

spandey@spandey-desktop:~$

---

