---
title: "Dual NIC Oddity"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by kerfurdt on 2011-05-12
While installing Ubuntu Server it acknowledges that I have 2 NIC and asks me to choose one.  I choose the GB card (intranet) and it is auto assigned to eth1.  After the install I define eth0 (internet). Here's a copy of my /etc/network/interfaces:

auto eth0 eth1 lo
iface lo inet loopback

iface eth0 inet static
  address XXX.XXX.XXX.149
  netmask 255.255.255.XXX
  network XXX.XXX.XXX.144
  broadcast XXX.XXX.XXX.151
iface eth1 inet static
  address 10.0.1.2
  netmask 255.255.255.0
  network 10.0.1.0
  broadcast 10.0.1.255
  gateway 10.0.1.1

dump of route -n:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
XXX.XXX.XXX.144  0.0.0.0         255.255.255.XXX U     0      0        0 eth0
10.0.1.0        0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         10.0.1.1        0.0.0.0         UG    100    0        0 eth1

I have a TX100 switch connected to the ISP's router and it is set to just bridge.  I have an ipcop box and this machine running FTP connected to both the TX100 switch and the intranet Gigabit switch.  Although both boxes are set up the same (2 interfaces, 1 intranet 10.0.1.XXX, one internet) from inside the office everything is well but I cannot receive incoming connections to the FTP server from outside the router.  I can and do get incoming connections on the ipcop box (can remote SSH in to it from home).  Any ideas?

---

