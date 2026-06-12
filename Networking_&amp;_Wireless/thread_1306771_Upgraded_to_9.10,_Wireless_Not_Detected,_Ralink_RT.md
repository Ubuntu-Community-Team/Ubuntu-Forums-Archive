---
title: "Upgraded to 9.10, Wireless Not Detected, Ralink RT2860, TrendNet TEW-621PC."
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by frmdstryr on 2009-10-30
Upgraded last night, was working perfectly in 9.04, with VPN and WPA2 connections (school).  Now the wireless card isn't detected.  The computer is a HP Pavilion dv5000, running 9.10 64-bit, kernel 2.6.31.14-generic.

heres my lshw -C network
```

 *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:c0204000-c0205fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:00:5a:fb
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.83 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:22 ioport:a000(size=256) memory:c020a400-c020a4ff
  *-network UNCLAIMED
       description: Network controller
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:07:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0 maxlatency=4 mingnt=2
       resources: memory:84000000-8400ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


```
(the first BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller is broken and isn't being used)
the 2nd to last is the wireless card

heres lspci -v
```

07:00.0 Network controller: RaLink RT2800 802.11n PCI
	Subsystem: RaLink Device 2860
	Flags: slow devsel, IRQ 20
	Memory at 84000000 (32-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Kernel modules: rt2860sta

```

from searching around i found this [396945 bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/396945"), that reported a patch to fix the driver that is supposed to be here  [http://www.ralinktech.com.tw/data/drivers/RT2860_Firmware_V11.zip]("http://www.ralinktech.com.tw/data/drivers/RT2860_Firmware_V11.zip") (the site just says not found)

any help is appreciated, so far i'm not liking 9.10 very much....

---

### Post by grantjohnston on 2009-11-02
> **frmdstryr said:**
> Upgraded last night, was working perfectly in 9.04, with VPN and WPA2 connections (school).  Now the wireless card isn't detected.  The computer is a HP Pavilion dv5000, running 9.10 64-bit, kernel 2.6.31.14-generic.

heres my lshw -C network
```

 *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:c0204000-c0205fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:00:5a:fb
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.83 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:22 ioport:a000(size=256) memory:c020a400-c020a4ff
  *-network UNCLAIMED
       description: Network controller
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:07:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0 maxlatency=4 mingnt=2
       resources: memory:84000000-8400ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


```
(the first BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller is broken and isn't being used)
the 2nd to last is the wireless card

heres lspci -v
```

07:00.0 Network controller: RaLink RT2800 802.11n PCI
	Subsystem: RaLink Device 2860
	Flags: slow devsel, IRQ 20
	Memory at 84000000 (32-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Kernel modules: rt2860sta

```

from searching around i found this [396945 bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/396945"), that reported a patch to fix the driver that is supposed to be here  [http://www.ralinktech.com.tw/data/drivers/RT2860_Firmware_V11.zip]("http://www.ralinktech.com.tw/data/drivers/RT2860_Firmware_V11.zip") (the site just says not found)

any help is appreciated, so far i'm not liking 9.10 very much....




Try this: [http://ubuntuforums.org/showpost.php?p=8211880&postcount=113](http://ubuntuforums.org/showpost.php?p=8211880&postcount=113)


Mine was working, I just wasn't getting the "N" speeds. Don't worry about the errors, I got them too!

---

### Post by frmdstryr on 2009-11-04
worked! thanks.  for some reason it won't connect unless i manually add the ip address and dns, what could be causing this?  Thanks.

---

### Post by solca on 2009-11-19
Hey guys, if you want 802.11n speeds check this [post]("http://ubuntuforums.org/showthread.php?p=8346399#post8346399").

---

