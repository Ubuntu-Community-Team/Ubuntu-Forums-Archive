---
title: "Dell Inspiron Ethernet/Wifi Problems"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by texasnomad on 2008-12-09
I installed Ubuntu - the internet ran flawlessly the first time.

I wanted to get the wifi up and running.  I switched to XP to copy some files, but when I went back to Ubuntu, the ethernet no longer worked.  I flipped back to XP and it doesn't work either.

I tried reconfiguring TCP/IP in XP.  Running netish under the command prompt generates errors about some missing .dll - could that really mess up Ubuntu as well?

I've been messing with this for days and am not sure where to turn next.  Should I focus efforts to resolve the issue in Ubuntu, XP or both?  Where to start?  Your guidance is appreciated.

---

### Post by superprash2003 on 2008-12-09
post output of ifconfig from the terminal

---

### Post by texasnomad on 2009-03-29
I have the ethernet up and running.  My problem is getting onto my home wireless network.  

The card identifies the network, but I can't figure out why it won't connect.  I give it the correct MAC address and WEP key, but it won't authenticate.  Directions would be much appreciated.


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:52:1b:62  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe52:1b62/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1872644 (1.8 MB)  TX bytes:407251 (407.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2200 (2.2 KB)  TX bytes:2200 (2.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0b:7d:18:a5:89  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0B-7D-18-A5-89-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

