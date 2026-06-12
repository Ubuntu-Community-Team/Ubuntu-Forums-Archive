---
title: "Fujitsu-Siemens Amilo Sa 3650 Wireless problem"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by QoccoQ on 2009-04-14
Hi, I recently bought a new laptop FS Amilo Sa 3650 with graphic booster. Everything works fine however I have wireless network issues. I cannot see or connect to any wireless network in the area and I know they work since I have no problem connecting to them in Windows. I'm using Ubuntu 8.10 64-bit.

This is the output of lshw -C network:

  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wmaster0
       version: 01
       serial: 00:15:af:cd:c7:f6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0f:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:10:8c:aa
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.10 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: da:16:20:3a:93:67
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

-----------------------------------------

and this is the output of lspci:

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:03.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 1)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
0e:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
0f:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
10:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
10:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
10:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
10:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
10:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

Hope someone will be able to help me out!

/QoccoQ

---

### Post by QoccoQ on 2009-04-15
bump

---

### Post by QoccoQ on 2009-04-15
nobody willing to help me?

---

### Post by chokecherry on 2009-05-19
Hi,  I registered just so I could help you :)  but I don't know how much help I can be.  I am working on the same Amilo with jaunty with a similar but slightly different wireless problem.

The initial fix is a bios update from the Fujistu website.  That will allow you to turn on your wireless.  As it was explained to me, the amilo is designed with software controls on the wireless and removing windows removes your "software" control.  It can be changed in the bios.  Unfortunately it doesn't have a hardware control ie a button or switch for this function.

Unfortunately I got that update in and now wireless will turn-on and connect but it will leave me with full "bars" registered but no connection in the background.  It may be (at this point I am hunting for an update to the wireless card now.

I don't know if this gives you a direction or is of any help - but I hope so!

---

### Post by jonas1980 on 2009-07-14
OT: but how did you install the GraphicBooster? I am having problem also with Ubuntu not finding wireless networks on my Fujitsu-Siemens AMILO Sa 3650 Notebook.

---

### Post by Houchy on 2010-05-24
Hi,

sorry it's a bit off topic but did you manage to get the graphicbooster to work?

Thank you.

---

