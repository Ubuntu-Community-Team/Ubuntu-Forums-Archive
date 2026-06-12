---
title: "Wired network problems"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by gabz8472 on 2009-04-29
I just installed Ubuntu 9.04 last weekend. Everything seemed to work fine except for two things - my wired lan isn't connecting at all, though I have no problems with my wireless, and when I tried using blender, something was wrong with the screen resolution. I tried looking at posts for blender, but can't make heads or tales out if it.
Anyway, my priority is my wired lan.

I'm using a lenovo y410 laptop.

I ran ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:1b:38:a7:81:b8  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fea7:81b8/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1088 (1.0 KB)  TX bytes:2460 (2.4 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3008 (3.0 KB)  TX bytes:3008 (3.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:ad:6c:df  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fead:6cdf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:290450 errors:0 dropped:0 overruns:0 frame:0
          TX packets:302278 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:302664193 (302.6 MB)  TX bytes:39238922 (39.2 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-AD-6C-DF-63-64-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

