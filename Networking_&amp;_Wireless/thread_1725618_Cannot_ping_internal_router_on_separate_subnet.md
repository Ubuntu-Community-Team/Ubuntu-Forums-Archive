---
title: "Cannot ping internal router on separate subnet"
date: 2011-04-09
forum: Networking &amp; Wireless
---

### Post by nethompson on 2011-04-09
Hey everyone, after much work that required very little, I finally got my first NIC with my public IP connected and an internal router on my second NIC connected properly. Now I have another...task that I would like to perform. How would I make it so that I am able to connect to my internal router from my server?

ppp0:

IP:             xx.xx.xxx.xxx
netmask:  255.255.255.252
GW:          xx.xx.xxx.xxx

eth1:

IP:            192.168.0.1
netmask:  255.255.255.0
GW:         127.0.0.1

Router (DHCP from eth1):

IP:            192.168.0.101
netmask:  255.255.255.0
GW:          192.168.0.1
DNS:         192.168.0.1

Routing table:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
ISP GW           0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         ISP GW            0.0.0.0         UG    0      0        0 ppp0

---

