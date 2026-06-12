---
title: "Splitting network traffic"
date: 2012-08-20
forum: Networking &amp; Wireless
---

### Post by poet_imp on 2012-08-20
- I have two network cards in my system. 
- I have two network connections 
- One network is a 10.xxx.xxx.xxx network and it is internal
- 0ne network is a 192.168.xxx.xxx and has access to the Internet
- Both networks can operate independently in that they both have access to a default gateway.
- I need to use DNS from the 10.xxx.xxx.xxx network

What I want to do is split traffic so that any 10.xxx.xxx.xxx address is directed to the one card and all other addresses are directed through the second card.

Is this possible and if so can someone help me with the setup?

---

### Post by poet_imp on 2012-08-21
I believe I have this working. My /etc/network/interfaces looks like:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface

auto eth0
iface eth0 inet static
        address 10.11.xx.xx
        netmask 255.255.0.0
        post-up route add -net 10.0.0.0 netmask 255.0.0.0 gw 10.11.xx.zz
        pre-down route del -net 10.0.0.0 netmask 255.0.0.0 gw 10.11.xx.zz

auto eth1
iface eth1 inet static
        address 192.168.1.xx
        netmask 255.255.255.0
        gateway 192.168.1.zz

All of my internal traffic is staying internal and my external traffic is getting routed outside.

The "zz" addresses point to gateway addresses. The "xx" addresses are static.

---

### Post by dandnsmith on 2012-08-22
I don't think you need to add and remove the route - just ensuring that the route exists for the 10. net is sufficient.
BTW the 192.168. and 10. networks are classed as private and are non-routable, so you don't need to worry about specific address quoting in a post as they are not available to the outside world.

---

