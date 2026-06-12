---
title: "Stuck/Did using bluetooth do something to wifi?"
date: 2013-02-16
forum: Networking &amp; Wireless
---

### Post by MyTinFoilHat on 2013-02-16
Recently reinstalled 12.10 from LiveCD and updated.
12.10 install went well. Drivers worked out-of-the-box.
I used wired connection to grab software & updates. 
After installation, I was able to see, connect, and use wifi networks. 
I ended up having to switch between wired and wifi for various reasons- still, no issues. Seemed solid. Everything worked well.

Connected my laptop to my smartphone via Bluetooth (couldn't find my mini USB). Pairing, connection, and file transfers between laptop and smartphone were all successful. No problems.

When I went to use wifi later on, no wifi networks appear. (Currently back on wired connection). Networking is enabled.

```

lshw -C network

```

shows me:

  *-network UNCLAIMED
       description: Network controller
       product: BCM4321 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d7300000-d7303fff
  *-network
       description: Ethernet interface
       product: 88E8058 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 13
       serial: 00:1e:c2:1c:5f:ca
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=192.168.1.10 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:d7200000-d7203fff ioport:5000(size=256) memory:dba00000-dba1ffff

```

lspci -vvnn | grep 14e4

```

shows me:

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 05)


I don't know what to do next. I'm concerned about the fact that wifi functionality simply "disappeared" (for lack of a better term). I'm wondering if my using Bluetooth somehow screwed things up and am wary of using it in the future if it means losing wifi again (once I get wifi working again).

Where do I go from here?


Thanks in advance!  :)

---

### Post by MyTinFoilHat on 2013-02-17
Anyone?

---

