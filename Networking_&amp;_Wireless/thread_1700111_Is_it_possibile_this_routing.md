---
title: "Is it possibile this routing?"
date: 2011-03-04
forum: Networking &amp; Wireless
---

### Post by Debie on 2011-03-04
Hi all,
I have a question about a strange routing configuration.
Let suppose to have this (strange) configuration:
 
Modem/Router
|
|
------host 192.168.0.2
|
|
------gateway A 192.168.0.3 eth0
10.10.0.254 eth1
|
|
gateway B 10.10.0.253 eth0
192.168.0.1 eth1
|
|
LAN 
 
To clarify:
The modem is connected only to gateway A and host 192.168.0.2.
The gateway A is connected with a direct link to gateway B.
The gateway B is connected to LAN.
 
All clients on LAN (192.168.0.0/24) are ok (internet, mail, forwading service).
I want to ping the host 192.168.0.2.
On router B I setted the routing "ip route add 192.168.0.2/32 via 10.10.0.254 dev eth0" and from gateway B I can ping that host but I can't from LAN.
 
Is it possible to ping that host with this configuration?
 
Thanks
 
(Unforntunately I can't change this configuration.)

---

### Post by Debie on 2011-03-05
No one have any idea?

---

