---
title: "Hawking HWUG1A wireless adapter problems!!#&amp;*$"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by b3ard on 2010-04-26
greetings to all, 

I have been stuck on this problem for the past two days, I just got an old HP/Compaq d530 desktop for free and it has no wireless capabilities. I also just a Hawking HWUG1A wireless adapter and plugged it in. I am running Ubuntu 8.04 ( 9.10 wouldn't even recognize the device) and the adapter is not picking up any networks. When I type in terminal "ifconfig", i get : 

<
eth0      Link encap:Ethernet  HWaddr 00:0e:7f:65:8f:bd  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:7fff:fe65:8fbd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:30002 errors:1 dropped:0 overruns:0 frame:24
          TX packets:19127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33061778 (31.5 MB)  TX bytes:2220623 (2.1 MB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:804 errors:0 dropped:0 overruns:0 frame:0
          TX packets:804 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40200 (39.2 KB)  TX bytes:40200 (39.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0e:3b:0e:91:39  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0E-3B-0E-91-39-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
>

so I know that it is being read and when I type "iwlist scan" I get :

< 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results
>

I would appreciate any help at all regarding this problem. I have looked online without any luck thus far.

---

