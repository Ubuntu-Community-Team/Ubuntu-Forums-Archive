---
title: "Cannot ping Default Gateway...Please help :-S"
date: 2012-08-20
forum: Networking &amp; Wireless
---

### Post by deadfish87 on 2012-08-20
Hey everyone, i know this has been written about a lot on here but no other post seems to help me.

I was struggling to connect to my wireless internet using automatic DHCP so decided to connect using manual allocation. This connected me to my wireless but for some reason i cannot ping my default gateway. Here is some info for people to look over:

ipconfig -a

eth0      Link encap:Ethernet  HWaddr bc:ae:c5:8d:5e:32  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:50 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4038 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4038 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:322173 (322.1 KB)  TX bytes:322173 (322.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:1f:fa:1a:69  
          inet addr:192.168.1.252  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:1fff:fefa:1a69/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2774 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:222247 (222.2 KB)  TX bytes:258276 (258.2 KB)
-----------------------------------------------------------------
ip route show

default via 192.168.1.254 dev wlan0  proto static 
169.254.0.0/16 dev wlan0  scope link  metric 1000 
192.168.1.0/24 dev wlan0  proto kernel  scope link  src 192.168.1.252  metric 2
-----------------------------------------------------------------
cat < /etc/resolv.conf

nameserver 127.0.0.1
search home
nameserver 192.168.1.254
-----------------------------------------------------------------

Thanks in advance! :p

---

