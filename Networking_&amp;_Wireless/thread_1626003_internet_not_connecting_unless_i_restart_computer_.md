---
title: "internet not connecting unless i restart computer several times"
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by Alphamonkey on 2010-11-19
Hi, I am having a problem with my internet connection. It only works half the time. Usually when i start the computer it doesn't connect until i restart anywhere from 1 - 10 times. I did sudo ifconfig while it was not working here is the output:

eth0      Link encap:Ethernet  HWaddr 00:19:d1:00:36:41  
          inet6 addr: fe80::219:d1ff:fe00:3641/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:660 (660.0 B)  TX bytes:5245 (5.2 KB)
          Interrupt:20 Memory:93200000-93220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)


and now while it is working:

eth0      Link encap:Ethernet  HWaddr 00:19:d1:00:36:41  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe00:3641/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1045 errors:0 dropped:0 overruns:0 frame:0
          TX packets:990 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1063478 (1.0 MB)  TX bytes:203771 (203.7 KB)
          Interrupt:20 Memory:93200000-93220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)


if anyone has any solution it would be greatly appreciated.

---

### Post by grahammechanical on 2010-11-19
In both cases ifconfig shows that eth0 is UP and RUNNING. So why are you not getting a connection? Notice the absence of the following line

> inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0

It is present when you are connected but not present when you are not connected. This information is collected by network manager when it connects to the router/modem.

I would be checking the router/modem. Is the power supply stable? Is the ethernet cable faulty? Things like this I would check.

regards.

---

