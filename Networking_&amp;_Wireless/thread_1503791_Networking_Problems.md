---
title: "Networking Problems"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by Ubapptu on 2010-06-07
Hi All,
I have 2 nic cards.  One I use for my LAN and the other for my WAN (ftp, web).  I am using a fresh install of Ubuntu 10.04 LTS.  If I disconnect the WAN I can download packages (apt-get), ping etc.  If both nic cards are active I cannot do either.  This behavior is the same whether or not iptables is enabled.  Any help would be greatly appreciated.  Oh BTW I am using the server version.  I was only able to find examples that used a GUI, nothing from the command line.

Here is my set up...

_**cat /etc/network/interfaces**_
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto eth0 eth1

iface eth0 inet static
address 192.168.1.185
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.2
broadcast 192.168.1.255


iface eth1 inet static
address ??.??.???.241
netmask 255.255.255.248
gateway ??.??.???.246
broadcast ??.??.???.247
pre-up iptables-restore < /etc/iptables.rules

**_route_**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
??.??.???.240   *               255.255.255.248 U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         adsl-??-??-???- 0.0.0.0         UG    100    0        0 eth1
default         192.168.1.2     0.0.0.0         UG    100    0        0 eth0

**_netstat -rn_**
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
??.??.???.240   0.0.0.0         255.255.255.248 U         0 0          0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         ??.??.???.246   0.0.0.0         UG        0 0          0 eth1
0.0.0.0         192.168.1.2     0.0.0.0         UG        0 0          0 eth0


Thanks in advance :)

---

### Post by Iowan on 2010-06-07
Having two gateways defined may be the problem - that's where "other traffic" is supposed to be sent (internet, in particular).

---

