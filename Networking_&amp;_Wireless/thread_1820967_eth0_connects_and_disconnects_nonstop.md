---
title: "eth0 connects and disconnects nonstop"
date: 2011-08-08
forum: Networking &amp; Wireless
---

### Post by mafi127 on 2011-08-08
in network manager I have set in wired connection to connect automaticly and in the ipv4 I have set "share to other computer". The computer where I share connection is my media center where I watch movies. but now the connection cant be made. The network manager just says connectiong to eth0 and then disconnected and so on... it just cant establys connection. I tryed whit two other computer as well, but the problem is still the same.

ifconfig
[PHP]pc@Mafia:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:27:13:68:05:75  
          inet6 addr: fe80::227:13ff:fe68:575/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4447 (4.4 KB)  TX bytes:54628 (54.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:622 errors:0 dropped:0 overruns:0 frame:0
          TX packets:622 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81955 (81.9 KB)  TX bytes:81955 (81.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:c6:82:b7:4a  
          inet addr:192.168.2.21  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::226:c6ff:fe82:b74a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10366 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5495 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6213930 (6.2 MB)  TX bytes:976981 (976.9 KB)

pc@Mafia:~$ 
[/PHP]

---

