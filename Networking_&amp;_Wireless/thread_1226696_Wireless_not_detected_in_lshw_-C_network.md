---
title: "Wireless not detected in lshw -C network"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by Bascal on 2009-07-29
Please help. I've done everything step by step by [this guide](http://ubuntuforums.org/showthread.php?t=1188702) and my wireless still won't connect.

Here is the result of sudo lshw -C network

  *-network
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 78
       serial: 00:01:03:31:d9:7d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.69.135 latency=32 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 02:b4:a4:9e:d3:e8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by dmizer on 2009-07-29
> **Bascal said:**
> Please help. I've done everything step by step by this guide and my wireless still won't connect.

Here is the result of sudo lshw -C network

  *-network
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 78
       serial: 00:01:03:31:d9:7d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.69.135 latency=32 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 02:b4:a4:9e:d3:e8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Doesn't look like your kernel is even detecting your wireless card. Do you know what card you have?

---

### Post by Bascal on 2009-07-29
It is a Linksys Wireless G w/ Speedbooster Broadcom 4318

Edit: wmp54gs

---

### Post by Bascal on 2009-07-29
Nevermind I ended up trouble shooting the problem myself. I went through BIOS and one of my PCI inputs had been turned off so I stopped that and switched the card to a new PCI just in case. So then it finally started seeing the card. The guide still didn't work though until after I went ->System->Administration->Hardware Drivers and activated the drivers but oh well at least I'm posting this wirelessly now! =)

Thanks anyway.

---

