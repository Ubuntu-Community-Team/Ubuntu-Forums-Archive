---
title: "Crash after /etc/network/interfaces restart"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by x ColdDeath x on 2010-12-26
I have such problem:
If I try the command 

**/etc/init.d/networking restart**

some times successively, them my system hangs and shows the following crash on the screen:
[ [IMG] http://i031.radikal.ru/1012/1d/94e186c50c45.jpg [/img] ](http://www.radikal.ru)
I think this is about memory.
As result - system in total lag and helps only Reset
My server have two network adapters: eth0 - builtin NIC, and eth1 - NIC on interface PCI - D-Link DGE-528T.
This problem is not depends of NIC hardware, because I tested different NICs (D-link DGE-510T and AMDTek an983b) on different PCI-slots and at different interfaces eth(i)

my file /etc/network/interfaces:

[B]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces (5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.0.1
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255

pre-up iptables-restore </etc/iptables.rules

auto eth1
iface eth1 inet static
    address 192.168.1.2
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255

auto dsl-provider
iface dsl-provider inet ppp
pre-up/sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider 
[/B]

I can not understand how to fix this problem. I think that problem in PPPoE, because when I removing these strings:
[B]
auto dsl-provider
iface dsl-provider inet ppp
pre-up/sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider 
[/B]
then reconfiguring of network interfaces is successfull!
But I want to hold pppoe on /etc/network/interfaces/.
Please, help me. I don't understand how to fix this problem.

System: Ubuntu 9.10
The kernel version: 2.6.31-22-server

---

