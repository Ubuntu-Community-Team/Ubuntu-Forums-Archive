---
title: "Discovering network printers and configuring routes."
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by Linfreak on 2010-04-06
Hi all,

1. My machine [running Karmic Koala] is part of a corporate LAN with NIC details below 
> 
eth0
   Link encap:Ethernet  HWaddr 00:19:b9:00:bc:50  
   inet addr:172.20.53.117 Bcast:172.20.63.255 Mask:255.255.240.0
   inet6 addr: fe80::219:b9ff:fe00:bc50/64 Scope:Link
   UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
   RX packets:166605 errors:0 dropped:0 overruns:0 frame:0
   TX packets:21446 errors:0 dropped:0 overruns:0 carrier:0
   collisions:0 txqueuelen:1000 
   RX bytes:39037470 (39.0 MB)  TX bytes:3488899 (3.4 MB)
   Interrupt:16

2. My routing table:
> Destination Gateway Genmask Flags Metric Ref Use Iface
172.20.48.0  0.0.0.0      255.255.240.0   U     0   0   0  eth0
0.0.0.0      172.20.48.1  0.0.0.0         UG    0   0   0  eth0


3. The network printer's details [as read from the printer's display interface]:
> 
IP:               172.20.254.158
Subnet mask:      255.255.255.128
Default gateway:  172.20.254.129


My question:

This printer can be discovered by windoze machines using "Find printers" and then added. [Am not sure how this works!]

But when I try to discover the same from my ubuntu machine, its not getting discovered. Tried pinging the ip [172.20.254.158] which gives the following:> 
PING 172.20.254.158 (172.20.254.158) 56(84) bytes of data.
From 172.20.48.2 icmp_seq=15 Packet filtered
From 172.20.48.2 icmp_seq=25 Packet filtered
^C
--- 172.20.254.158 ping statistics ---
27 packets transmitted, 0 received, +2 errors, 100% packet loss, time 26071ms

Now I tried fiddling around with the route command along with good amount of googling but to no avail.

1. Is there a way I could add that printer to my machine?
2. If yes, how could I? Does it involve adding routes?

Kindly give any steps necessary. Am willing to provide any additional details if it helps.

Thanks.

---

### Post by Iowan on 2010-04-06
I haven't done any large-scale networking, but my systems have all machines with the same subnet mask. Your printer uses 255.255.255.128, but the Karmic machine uses 255.255.240.0. What is the Windows machine using for netmask?

---

### Post by Linfreak on 2010-04-07
The subnet of the windows machine is also 255.255.240.0

I am assuming "Find printers" actually gets the list from some other printer server. And this authenticates the user and his print privileges.

HTH.

---

