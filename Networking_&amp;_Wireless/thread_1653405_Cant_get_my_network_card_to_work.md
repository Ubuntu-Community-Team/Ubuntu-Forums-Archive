---
title: "Cant get my network card to work"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by ialvik on 2010-12-26
Hi.

when I use the command lshw -c network  I get this output. 

[QUOTE][  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82566DM-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: latency=0
       resources: memory:d0300000-d031ffff memory:d0327000-d0327fff ioport:1820(size=32)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: 00:11:50:e7:98:f0
       size: 1GB/s
       capacity: 1GB/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion=14-Jun-2006 duplex=full firmware=ASIX AX88178 USB 2.0 Ethernet ip=10.0.0.9 link=yes multicast=yes port=MII speed=1GB/s
/QUOTE]

Just cant figure out what that is the problem with the  82566DM-2 network card?

---

### Post by dineshs on 2010-12-27
From lshw output(network unclaimed) your device is > product: 82566DM-2 Gigabit Network Connection and the driver loaded is > driver=asix driverversion=14-Jun-2006 duplex=full firmware=ASIX AX88178 USB 2.0 I think(not sure) it is a driver issue.Pl see
[http://nixcraft.com/linux-hardware/11898-need-help-installing-linux-drivers-intel-r-82566dm-2-gigabit-ethernet-connection.html](http://nixcraft.com/linux-hardware/11898-need-help-installing-linux-drivers-intel-r-82566dm-2-gigabit-ethernet-connection.html)

---

### Post by ialvik on 2010-12-29
Does not seem there is any drivers installed at all :confused:  

The drivers you refer to are for my USB-network device that is working :) 

But thanks for the link :)

---

### Post by ialvik on 2010-12-30
But still cant get it to work :/

Maybe there is some problems with 64-bit drivers yet?

---

