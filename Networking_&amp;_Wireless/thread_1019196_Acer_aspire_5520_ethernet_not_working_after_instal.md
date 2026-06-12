---
title: "Acer aspire 5520 ethernet not working after installing madwifi"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by cammpopp on 2008-12-22
Thanks for your useful tutorial on how to install the madwifi driver for atheros card.I have acer aspire 5520 and ubuntu 8.04 and am successfully using my wireless card but my nVidia Corporation MCP67 Ethernet card does not work after installing madwifi driver. I also do not see wired network in my connection manager and i would be thankful if u can help me out with it

###########################################
root@hardy:~# [COLOR="Red"]ifconfig[/COLOR]

ath0 Link encap:Ethernet HWaddr 00:1f:3a:48:d1:68
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:178 errors:0 dropped:0 overruns:0 frame:0
TX packets:178 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:8900 (8.6 KB) TX bytes:8900 (8.6 KB)

wifi0 Link encap:UNSPEC HWaddr 00-1F-3A-48-D1-68-00-00-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:511 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:280
RX bytes:0 (0.0 B) TX bytes:23506 (22.9 KB)
Interrupt:21
####################################
root@hardy:~# [COLOR="Red"]ifconfig eth0 up[/COLOR]
eth0: ERROR while getting interface flags: No such device
########################################
root@hardy:~# [COLOR="Red"]lshw -C network
[/COLOR]
*-network UNCLAIMED
description: Ethernet controller
product: MCP67 Ethernet
vendor: nVidia Corporation
physical id: a
bus info: pci@0000:00:0a.0
version: a2
width: 32 bits
clock: 66MHz
capabilities: pm msi ht bus_master cap_list
configuration: latency=0 maxlatency=20 mingnt=1
*-network
description: Wireless interface
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:05:00.0
logical name: wifi0
version: 01
serial: 00:1f:3a:48:d1:68
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

###########################################
root@hardy:~# [COLOR="Red"]lspci[/COLOR]

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

