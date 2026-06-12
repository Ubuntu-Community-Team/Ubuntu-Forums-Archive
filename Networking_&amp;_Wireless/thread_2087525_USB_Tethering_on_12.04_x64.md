---
title: "USB Tethering on 12.04 x64"
date: 2012-11-23
forum: Networking &amp; Wireless
---

### Post by lowriderdog37 on 2012-11-23
I have been trying to run USB tethering using Ubuntu 12.04 on two laptops with a pair of Rooted Droid X phones running AOKP and MIUI ROMs.  [ifconfig -a] doesn't show USB0 at all.  I have done many searches and no progress.  

For whatever reason, Wifi tethering won't activate and would rather USB anyways.  Thoughts?

ifconfig -a:
> eth0      Link encap:Ethernet  HWaddr 00:13:a9:c4:10:8d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2041 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2041 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:151648 (151.6 KB)  TX bytes:151648 (151.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:7a:85:e1  
          inet addr:192.168.2.104  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fe7a:85e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4626 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3570650 (3.5 MB)  TX bytes:677304 (677.3 KB)


---

