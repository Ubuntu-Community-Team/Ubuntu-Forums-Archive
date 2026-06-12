---
title: "Routing for multiple uplinks/Providers"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by baidaraka on 2009-02-15
Hi,

according to the under mentioned url i did all but still problem in routing 2 isps on same linux router,
[http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html)


Using Ubunut hardy 8.04 server i386
My /etc/network/interfaces
> 

---------------------
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
# gateway 192.168.1.1
auto eth2
iface eth2 inet static
address 192.168.2.2
netmask 255.255.255.0
network 192.168.2.0
# gateway 192.168.2.1

auto eth0
iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
-------------------------


According to [http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html)

> 

#!/bin/sh

## Creating Routing Tables
ip route add 192.168.1.0 dev eth1 src 192.168.1.2 table 1
ip route add default via 192.168.1.1 table 1
ip route add 192.168.2.0 dev eth2 src 192.168.2.2 table 2
ip route add default via 192.168.2.1 table 2
#=====
ip route add 192.168.1.1 dev eth1 src 192.168.1.2
ip route add 192.168.2.1 dev eth2 src 192.168.2.2
# default route
ip route add default via 192.168.1.1
# Adding Rules
ip rule add from 192.168.1.2 table 1
ip rule add from 192.168.2.2 table 2
# Adding according to Rod roard Note
ip route add 192.168.0.0 dev eth0 table 1
ip route add 192.168.2.0 dev eth2 table 1
ip route add 127.0.0.0/8 dev lo table 1

ip route add 192.168.0.0 dev eth0 table 2
ip route add 192.168.1.0 dev eth1 table 2
ip route add 127.0.0.0/8 dev lo table 2

ip route add default scope global nexthop via 192.168.1.1 dev eth1 weight 1 nexthop via 192.168.2.1 dev eth2 weight 1
-------------------------------

My routes
> 

route -n

Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.1.1 0.0.0.0 255.255.255.255 UH 0 0 0 eth1
192.168.2.1 0.0.0.0 255.255.255.255 UH 0 0 0 eth2
192.168.2.0 0.0.0.0 255.255.255.0 U 0 0 0 eth2
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
192.168.0.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 eth1
root@playzone:~#

---------------------------------------

on my linux Router i can browse (using elinks)and surf internet with gateway 192.168.1.1 but when i unpluge the 192.168.1.1 then 192.168.2.1 is not working,
in elinks browser i open ubuntu.com its says "Unable to retrive [http://ubuntu.com/:](http://ubuntu.com/:) No route to host"


also i disable the line "
ip route add default via 192.168.1.1" but still some pages are opening and some not,
my linux routuer can ping each gateway,
any help??
there was old thread about multiple routing on linuxpakistan.net forum and i searched that but i was not lucky

---

