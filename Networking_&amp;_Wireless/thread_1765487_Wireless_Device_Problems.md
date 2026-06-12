---
title: "Wireless Device Problems"
date: 2011-05-23
forum: Networking &amp; Wireless
---

### Post by frozonecom on 2011-05-23
I am using a Sony Vaio laptop and the wireless device seems to have some malfunctions. The device is working and I have tested it. But, the problem is, whenever I turn the Wireless Device off, and then turn it on again, there will be a text "The hardware device has disabled wireless network." ~something like that.

It seems that Ubuntu cannot detect whether the switch is at "on" or "off".

I am running Ubuntu 11.04 and when I run

```
[COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C][FONT=monospace]sudo lshw -C network[/FONT][/COLOR][/FONT][/COLOR]
```This is the result:

```
*-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:1a:80:ba:9e:19
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=112.200.141.90 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:f6000000-f6003fff ioport:2000(size=256)
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 00:1d:d9:df:de:8d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:fa000000-fa00ffff

```I am hoping someone can help me with this problem.

And, the switch(for wifi) has lights when it's on when I try it on Vista. Here at ubuntu, no lights are seen.

---

### Post by frozonecom on 2011-05-30
bummmppp.............

---

