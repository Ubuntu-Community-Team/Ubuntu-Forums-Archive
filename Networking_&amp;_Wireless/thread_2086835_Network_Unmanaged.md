---
title: "Network Unmanaged"
date: 2012-11-22
forum: Networking &amp; Wireless
---

### Post by Redalien0304 on 2012-11-22
My Wired network is unmanaged on Dell Latitude D600. The wireless on/off but thats normal cause of range where im at. The Wired was Managed Before a Reinstall of Ubuntu 12.4 via a Netboot Mini iso Non-PAE. My wired Does work it is Fast/Slow & being Unmanaged bugs me.
here is the output of sudo lshw -class network

*-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:a5:fe:01
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=5705-v3.16 ip=192.168.1.101 latency=32 link=yes mingnt=64 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:11 memory:faff0000-faffffff
  *-network:1
       description: Network controller
       product: BCM4306 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:fafee000-fafeffff
  *-network DISABLED

here is the output of cat /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

any help or ideas appreciated Thanks

---

### Post by steeldriver on 2012-11-22
That's the default behavior for interfaces that are defined in /etc/network/interfaces (i.e. network-manager ignores them - it lets the older networking / ifupdown mechanism handle them) - if you want to use network-manager for everything best to comment out (or remove) the eth0 stanza from that file

---

### Post by Redalien0304 on 2012-11-24
Solved. Got a new 80Gb HDD Installed 11.10 ubuntu Upgraded to 12.4. no problems

---

