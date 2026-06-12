---
title: "default route"
date: 2011-08-17
forum: Networking &amp; Wireless
---

### Post by shadowskippie on 2011-08-17
afternoon

i need help with something, it involves a ubuntu server and a Wan network.

first off, an exert from my server --

> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.253.0   *               255.255.255.0   U     0      0        0 eth1
default         192.168.253.1   0.0.0.0         UG    0      0        0 eth1
radius@radius:~$


you see that default network, every time i restart the machine i have to manual add that route or the outside network cannot get hold of the server.

how do i make that permanent.

I have read information about this and it says add gateway into the interfaces conf file but i have it there, hell it was the first this i setup

> auto eth1
iface eth1 inet static
        address 192.168.253.8
        netmask 255.255.255.0
        network 192.168.253.0
        broadcast 192.168.253.255
        gateway 192.168.235.1


please, this is starting to annoy me, if any one can help

---

