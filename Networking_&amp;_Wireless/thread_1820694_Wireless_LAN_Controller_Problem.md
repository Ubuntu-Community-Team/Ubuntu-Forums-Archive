---
title: "Wireless LAN Controller Problem"
date: 2011-08-07
forum: Networking &amp; Wireless
---

### Post by Wasagi on 2011-08-07
I recently installed Ubuntu, and am a complete novice. My Broadcom BCM4138 isn't turned on by Ubuntu. I did a ```
sudo lshw -C network 
``` check, and it says that I'm missing firmware. I initially thought it was the driver, but that's present. Here's the check:
```
~$ sudo lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0204000-c0205fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:0c:9c:db
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:22 ioport:a000(size=256) memory:c020a400-c020a4ff
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:a7:5a:ed
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-10-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
```

Any ideas or help? Thanks!

---

### Post by bkratz on 2011-08-08
> **Wasagi said:**
> I recently installed Ubuntu, and am a complete novice. My Broadcom BCM4138 isn't turned on by Ubuntu. I did a ```
sudo lshw -C network 
``` check, and it says that I'm missing firmware. I initially thought it was the driver, but that's present. Here's the check:
```
~$ sudo lshw -C network
  *-network:0             
       description: Network controller
       product:[COLOR="Red"] BCM4318 [AirForce One 54g] 802.11g Wireless[/COLOR] LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0204000-c0205fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:0c:9c:db
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:22 ioport:a000(size=256) memory:c020a400-c020a4ff
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:a7:5a:ed
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-10-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
```

Any ideas or help? Thanks!


See post two in this thread

[http://ubuntuforums.org/showthread.php?t=1803825](http://ubuntuforums.org/showthread.php?t=1803825)

---

