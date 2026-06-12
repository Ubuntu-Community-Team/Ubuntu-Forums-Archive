---
title: "RTNETLINK answers: File exists Failed to bring up eth0."
date: 2013-04-18
forum: Networking &amp; Wireless
---

### Post by willholt89 on 2013-04-18
Hi Guys,

Currently an ubuntu noob, looking into doing some linux networking. I have a machine with an onboard NIC and 2 seperate ones installed. The two seperate ones will not come online. Also i cannot update the machines as i get the following error

Temporary failure resolving âsecurity.ubuntu.comâ

This is my current setup from /etc/hosts/network interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth2 eth1 eth0
iface eth2 inet static
           address 10.0.0.28
           gateway 10.0.0.3
           netmask 255.255.255.0
           network 10.0.0.0
           broadcast 10.0.0.255
           nameserver 10.0.0.3 8.8.8.8


iface eth1 inet static
           address 10.0.2.171
           gateway 10.0.2.50
           netmask 255.255.255.0
           network 10.0.2.0
           broadcast 10.0.0.255
           nameserver 10.0.2.150


iface eth0 inet static
           address 10.0.2.170
           gateway 10.0.2.50
           netmask 255.255.255.0
           network 10.0.2.0
           broadcast 10.0.0.255
           nameserver 10.0.2.150


Any help will be appreciated

---

### Post by steeldriver on 2013-04-18
This is above my paygrade but there was a similar post recently and iirc the issue turned out to be that you can't have multiple default gateways with the same metric 

[https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1043244/comments/8](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1043244/comments/8)

Hope this points you in the right direction

---

