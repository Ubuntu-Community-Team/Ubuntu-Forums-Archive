---
title: "Icon said networking disabled but my Internet is working"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by reychun on 2010-10-10
And I can't upgrade to Ubuntu 10.10 because it said that there's a problem with my network connection. When there's none, since I am typing this now. 

This is what ifconfig -a says about it:

eth0      Link encap:Ethernet  HWaddr 90:fb:a6:2f:35:78  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::92fb:a6ff:fe2f:3578/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3593 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2355 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:3115765 (3.1 MB)  TX bytes:281108 (281.1 KB)
          Memory:f9fc0000-f9fe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

PLEASE HELP! I want to upgrade to 10.10.

---

### Post by Iowan on 2010-10-10
I presume you got [this]("http://ubuntuforums.org/showthread.php?t=1497078") problem solved (or it is a different computer). Did you use Network Manager or */etc/network/interfaces* to set up interface?

(Although it *shouldn't* affect an upgrade :confused: )

---

### Post by reychun on 2010-10-10
It wasn't really solved. I just disabled the wireless networks to make sure it went towards my ethernet. But it disrupts my update manager when I want to check... so some things are not downloaded.

---

