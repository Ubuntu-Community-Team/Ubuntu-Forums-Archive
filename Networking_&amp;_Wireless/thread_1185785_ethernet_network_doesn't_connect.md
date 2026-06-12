---
title: "ethernet network doesn't connect"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by rebelxt on 2009-06-12
I have a two-computer wired ethernet network.  A desktop computer dual-boots WinXP and Ubuntu 9.04.  It has two ethernet ports, eth0 connected to a DSL modem, eth1 connected to a laptop.  The laptop also dual-boots WinXP and Ubuntu 9.04.

When the desktop is booted into WinXP, the laptop can connect to the internet just fine.  When the desktop is booted into Ubuntu, a "wired network disconnected" message appears, and the laptop can't see the internet.  This leads me to believe the problem is in the desktop Ubuntu system.  

I haven't seen what looks like a solution for me in any other thread, but I am inexperienced in Linux, so may not recognise the relevance.  The following information may be helpful:

```
sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x000000ff (255)
	Link detected: yes
```

```
sudo ethtool eth1
Settings for eth1:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pg
	Wake-on: g
	Current message level: 0x00000037 (55)
	Link detected: yes
```


```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:18:f3:6d:24:d8
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.64 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 4
       bus info: pci@0000:05:04.0
       logical name: eth1
       version: 14
       serial: 00:18:f3:6d:23:ac
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A latency=64 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=1GB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:09:c7:22
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ca:d1:c6:fe:8f:4d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

```
lspci -v
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
	Subsystem: SysKonnect Device 4340
	Flags: bus master, fast devsel, latency 0, IRQ 2299
	Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 9800 [size=256]
	Expansion ROM at fe8c0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

05:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)
	Subsystem: ASUSTeK Computer Inc. Device 811a
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at feaf4000 (32-bit, non-prefetchable) [size=16K]
	I/O ports at b800 [size=256]
	Expansion ROM at 88000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: skge
	Kernel modules: skge

[FONT="Arial"]*[COLOR="DeepSkyBlue"]I am assuming this is the only relevant information from this command.[/COLOR]*[/FONT]
```

Thanks for any help you can give.

---

### Post by Iowan on 2009-06-12
I'm still hoping "it ain't so", but last report I read suggests Network Manager still only manages one interface at a time.  You might be able to set up your interfaces in */etc/network/interfaces* and restart via **sudo /etc/init.d/networking restart**

---

