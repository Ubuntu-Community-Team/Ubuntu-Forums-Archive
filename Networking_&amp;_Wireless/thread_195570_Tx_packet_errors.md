---
title: "Tx packet errors"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by bionnaki on 2006-06-13
I am just curious what a tx packet error is. Is this bad? Is there a solution to reduce the errors? do they even matter?

here's the output of ifconfig:

> ra0       Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:192.168.1.xx  Bcast:xx.xx.x.xx  Mask:xxx.xxx.xxx.x
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45009 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40339 errors:20 dropped:20 overruns:0 carrier:0
          collisions:10086 txqueuelen:1000
          RX bytes:45839383 (43.7 MiB)  TX bytes:13422287 (12.8 MiB)
          Interrupt:217 Base address:0x4000


just wondering.
thanks.

---

### Post by easytiger on 2006-09-17
I too am getting this error. 

gerry@zanussi:~$ lspci | grep Ra
0000:00:06.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)

Ifconfig:
ra0 .....
TX packets:1865604 errors:1246 dropped:1246 overruns:0 carrier:0
...


Has anyone worked out what this is? It killing my connection. Things get so slow, new TCP requests take ages to form. Is a real pain.

---

