---
title: "Wireless card is disabled"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by J_86 on 2010-05-03
Hi, I just installed Ubuntu desktop 10.04. Going great so far, but I can seem to get my wireless adapter working. It is showing it, but it says it is disabled. I'm new to Linux, so I believe it is something simple

The adapter is a : Linksys WUSB100

ifconfig it shows:
eth0      Link encap:Ethernet  HWaddr 00:14:38:13:5c:c0  
          inet addr:10.2.1.83  Bcast:10.2.255.255  Mask:255.255.0.0
          inet6 addr: fe80::214:38ff:fe13:5cc0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27673 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19042248 (19.0 MB)  TX bytes:812718 (812.7 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1039 (1.0 KB)  TX bytes:1039 (1.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:db:6e:90  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


I tried ifconfig wlan0 up , but that didn't seem to do anything. Can someone point in the the right direction, what am I missing?

---

