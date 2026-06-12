---
title: "nic card problem"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by nsusheelgoud on 2011-11-09
when i inset net cabble its not detecting and not even showing interface



ifconfig -a:
root@susheel-laptop:~# ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:0c:f1:47:4f:ea  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Memory:fafff000-faffffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:42.107.131.237  P-t-P:10.6.6.6  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:10418 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11969 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:8784730 (8.7 MB)  TX bytes:1638625 (1.6 MB)

usbpn0    Link encap:UNSPEC  HWaddr 1B-00-FF-FF-FF-FF-00-00-00-00-00-00-00-00-00-00  
          POINTOPOINT NOARP  MTU:65541  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

