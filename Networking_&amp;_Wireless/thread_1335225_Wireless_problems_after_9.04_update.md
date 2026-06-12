---
title: "Wireless problems after 9.04 update"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by choopity on 2009-11-23
Hey!

About 2 days ago I ran update manager and a bunch of updates were installed. At first, my computer showed a wireless device that wasn't detecting the wireless network. Now, my computer is not detecting wlan0 at all! this is the output of ifconfig. I am completely lost in Linux so please help me out.

eth0      Link encap:Ethernet  HWaddr 00:26:18:21:8d:b9  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:18ff:fe21:8db9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3794 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:3885024 (3.8 MB)  TX bytes:714661 (714.6 KB)
          Interrupt:251 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:848 (848.0 B)  TX bytes:848 (848.0 B)

and iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

Anybody have any ideas?

---

