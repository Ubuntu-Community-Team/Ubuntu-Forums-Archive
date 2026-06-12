---
title: "Wireless Network Disabled?"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by SESU on 2010-04-22
I've recently installed Xubuntu Karmic on my Gateway MT6451, and I've been having difficulities with getting the wifi set up.
 
When I type in: lshw -C Network I get this back:> 
[SIZE=3][FONT=Times New Roman]*-network [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]description: Ethernet interface[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]product: 88E8038 PCI-E Fast Ethernet Controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]vendor: Marvell Technology Group Ltd.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]physical id: 0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]bus info: pci@0000:02:00.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]logical name: eth0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]version: 14[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]serial: 00:e0:b8:d3:8c:fd[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]width: 64 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]clock: 33MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]capabilities: bus_master cap_list ethernet physical[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]configuration: broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 multicast=yes[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]resources: irq:16 memory:c0200000-c0203fff ioport:a000(size=256)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*-network[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]description: Network controller[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]product: BCM4311 802.11b/g WLAN[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]vendor: Broadcom Corporation[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]physical id: 0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]bus info: pci@0000:05:00.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]version: 01[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]width: 32 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]clock: 33MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]capabilities: bus_master cap_list[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]configuration: driver=b43-pci-bridge latency=0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]resources: irq:17 memory:c0300000-c0303fff[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]***-network DISABLED**[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**description: Wireless interface**[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**physical id: 2**[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**logical name: wlan0**[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**serial: 00:1a:73:27:fe:49**[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**capabilities: ethernet physical wireless**[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg**[/FONT][/SIZE]
 

 
The bolded one at the bottom is where I'm having my problems. Does anyone know how to enable my wireless interface so that the network manager I have installed (wicd) will recognize it?

---

### Post by 2hot6ft2 on 2010-04-22
> product: **BCM4311** 802.11b/g WLAN

[The Definitive 9.10 Broadcom Solution Guide]("http://ubuntuforums.org/showthread.php?t=1368699")

And you currently have this driver installed
**driver=b43**

I'm not seeing another wifi device there.
If there's another one besides the Broadcom
then
If internal PCI
```
lspci
```
That's LSPCI in lower case, and post the results.

If it's a USB adapter
```
lsusb
```
That's LSUSB in lower case, and post the results.

---

