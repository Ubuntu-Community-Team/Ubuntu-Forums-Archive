---
title: "Wireless problems"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by Ramiska on 2009-11-20
Hi everyone I have problem with my wireless. It periodically disconnects from wireless network. here ifconfig output:

eth0      Link encap:Ethernet  HWaddr 00:16:36:a1:d3:4a  
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
          RX packets:727 errors:0 dropped:0 overruns:0 frame:0
          TX packets:727 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22614 (22.6 KB)  TX bytes:22614 (22.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:48:bf:d6  
          inet addr:192.168.1.124  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe48:bfd6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46018 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45300001 (45.3 MB)  TX bytes:6391219 (6.3 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-48-BF-D6-34-38-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

I'm using acer travelMate 3260 with Ubuntu 9.10

**lspci | grep Network**

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

---

