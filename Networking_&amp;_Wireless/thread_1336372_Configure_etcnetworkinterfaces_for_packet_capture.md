---
title: "Configure /etc/network/interfaces for packet capture"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by sdutky on 2009-11-24
I have a karmic desktop with dhcp for eth0. I have eth1 and eth2 connected to monitor ports on two different cisco layer 3 switches. 

I would like configure /etc/network/interfaces so that upon boot eth1 and eth2 get turned up preferably without ip addresses.

If I leave them out of /etc/network/interfaces and they have link up, they get assigned dhcp addresses presumably by way of eth0.

Currently, /etc/network/interfaces:

> 
#$Log: interfaces,v $
#Revision 1.2  2009/11/24 16:11:33  root
#eth1&2 static
#


auto lo eth1 eth2
iface lo inet loopback

iface eth1 inet static
        address 169.254.63.251
        netmask 255.255.255.255
        up

iface eth2 inet static
        address 169.254.63.252
        netmask 255.255.255.255
        up
With this, eth0 gets its normal ip address. eth1 and eth2 boot up down and unmanaged.

I can ifconfig eth[12] up and go about my business, but I would prefer having this happen as part of boot.

Any suggestions greatly appreciated.

---

### Post by Iowan on 2009-11-24
I haven't used it (therefore, don't really know anything about it), but check the "manual" option for the "iface" line.

---

