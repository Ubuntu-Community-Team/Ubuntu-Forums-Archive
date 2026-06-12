---
title: "routing help needed"
date: 2012-01-13
forum: Networking &amp; Wireless
---

### Post by nagileon on 2012-01-13
Hi there

wlan0 is connected to 192.168.0.0
eth0 is connected to 10.10.0.0

I can ping 10.10.0.10
I can't ssh to it 


pkirk ~ # route
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
ddns001bri.loca * 255.255.255.255 UH 0 0 0 eth0
192.168.0.0 * 255.255.255.0 U 2 0 0 wlan0
10.10.0.0 * 255.255.0.0 U 1 0 0 eth0
link-local * 255.255.0.0 U 1000 0 0 wlan0
default 192.168.0.1 0.0.0.0 UG 0 0 0 wlan0


ddns001bri.loca = 10.10.0.10


pkirk ~ # ping 10.10.0.10
PING 10.10.0.10 (10.10.0.10) 56(84) bytes of data.
64 bytes from 10.10.0.10: icmp_req=1 ttl=64 time=1.27 ms

pkirklewski ~ # ssh 10.10.0.10 -p 3103
ssh: connect to host 10.10.0.10 port 3103: No route to host

What do I do to fix this please ?

---

### Post by jonobr on 2012-01-13
If you have ssh on the server and can ping it, it sounds like the problem is firewall related.

Default action for IPtables is to respond with no route to host.

---

