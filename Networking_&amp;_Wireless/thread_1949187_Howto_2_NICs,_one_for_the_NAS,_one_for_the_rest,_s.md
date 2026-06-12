---
title: "Howto? 2 NICs, one for the NAS, one for the rest, same subnet"
date: 2012-03-29
forum: Networking &amp; Wireless
---

### Post by Fotograf81 on 2012-03-29
Hi all,

I recently bought a QNAP NAS and am now trying to get the most out of it.

I've got a linux server with two GBit NICs and would like to connect them to the same Switch using the same /24 subnet. One should be used to connect to the NAS, the other one should be used for everything else.

It has to be the same subnet, because the NAS should also be accessible from all other computers on the network, which only have one NIC.


I've tried some things with iptables but either no traffic went through the second NIC or the NAS wasn't reachable by any means from the server.


The IP-Addresses are set up as follows:

Server-NIC-1 (eth2): 192.168.0.1  (static)
Server-NIC-2 (eth3): 192.168.0.4  (static)
Router (and DNS, DHCP): 192.168.0.2 (static)
NAS: 192.168.0.3 (static)

All other Hosts on network: 192.168.0.100 and above (dynamic)




Does anyone know the correct way to achieve this?
routes? rules? a very narrow subnet for the NAS and eth3?



Thank you very much in advance!

---

