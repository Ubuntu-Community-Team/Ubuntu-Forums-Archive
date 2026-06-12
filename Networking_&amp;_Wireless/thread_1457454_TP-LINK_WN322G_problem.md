---
title: "TP-LINK WN322G problem"
date: 2010-04-18
forum: Networking &amp; Wireless
---

### Post by DaDoT on 2010-04-18
Hi everyone,

I install Ubuntu 9.10 on my nootbook HP compaq nx9105, everything is ok except WIFI (TP-LINK WN322G power L.E.D **is off**).

I install win drivers "netathur" but I recieve an error message saying 'Unable to see if hardware is  present'. When I press OK, the window disappear and the windows  wireless driver window show my driver installed and that the hardware is present.

When I open Hardware Drivers it says "No proprietary drivers are in use on this system."

When I type lshw -C network
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL -8139/8139C/8139C+
       vendor: Realtek Semiconductor Co.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:3f:29:18
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet 
physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too
 driverversion=0.9.28 duplex=full 
 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes
 port=MII speed=100MB/s
resources:irq18 ioport7000(size256) memory:e8106800-e81068ff


When I run ndiswrapper -l it says the driver is installed, device (0CF3:1006) present 

Please help,

tnx

---

