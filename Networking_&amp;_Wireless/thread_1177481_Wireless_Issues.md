---
title: "Wireless Issues"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by PostWax on 2009-06-03
_**Below is a copy of an earlier post this week.  My attempt here is to bring my problem back to the front.  If there is a better way of doing this please let me know.**_

I have been using Ubuntu for about a year now but still a newbee. Every version I have used 7.XX to 9.04 my wireless does not work well. I have to reboot the computer several times until finally it will log on to my secure router [WPA]. The machine is a dual boot, the Windows boot never a problem with wireless. Since I did not buy a name brand wireless card I have to use ndiswrapper and the Windows driver. 

I have read most of the threads regarding my problem but I can not seem to find a solution.

How do I check if I have a software conflict with my wireless?

[COLOR="LightBlue"]I do not seem to have a problem with a non secure router[/COLOR]

[COLOR="#add8e6"]Could my problem be with Network Manager?  I have tried WICD with no luck.  Any suggestion on a different Network Manager?[/COLOR]

My output of lshw -C network

*-network:0 
description: Wireless interface
product: 88w8335 [Libertas] 802.11b/g Wireless
vendor: Marvell Technology Group Ltd.
physical id: 1
bus info: pci@0000:01:01.0
logical name: wlan0
version: 03
serial: 08:10:73:0b:fa:8f
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+netmw126 driverversion=1.53+Customer,12/30/2005,3.2.3.2 ip=192.168.10.3 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
*-network:1
description: Ethernet interface
product: 88E8001 Gigabit Ethernet Controller
vendor: Marvell Technology Group Ltd.
physical id: 4
bus info: pci@0000:01:04.0
logical name: eth0
version: 14
serial: 00:1a:92:95:86:23
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=64 maxlatency=31 mingnt=23 module=skge multicast=yes
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 2a:e9:bb:02:a8:fc
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3
firmware=N/A multicast=yes

My output of lspci -v
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
Subsystem: ASUSTeK Computer Inc. Device 817a
Flags: bus master, fast devsel, latency 0
Capabilities: <access denied>
Kernel modules: intel-agp

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
Subsystem: ASUSTeK Computer Inc. Device 8249
Flags: bus master, fast devsel, latency 0, IRQ 19
Memory at dbef8000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
I/O behind bridge: 0000e000-0000efff
Memory behind bridge: dc000000-dfffffff
Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
Capabilities: <access denied>
Kernel driver in use: pcieport-driver
Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
Subsystem: ASUSTeK Computer Inc. Device 8179
Flags: bus master, medium devsel, latency 0, IRQ 20
I/O ports at a000 [size=32]
Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
Subsystem: ASUSTeK Computer Inc. Device 8179
Flags: bus master, medium devsel, latency 0, IRQ 17
I/O ports at a400 [size=32]
Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
Subsystem: ASUSTeK Computer Inc. Device 8179
Flags: bus master, medium devsel, latency 0, IRQ 18
I/O ports at a800 [size=32]
Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
Subsystem: ASUSTeK Computer Inc. Device 8179
Flags: bus master, medium devsel, latency 0, IRQ 19
I/O ports at b000 [size=32]
Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)
Subsystem: ASUSTeK Computer Inc. Device 8179
Flags: bus master, medium devsel, latency 0, IRQ 20
Memory at dbeffc00 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>
Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01)
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
I/O behind bridge: 0000d000-0000dfff
Memory behind bridge: dbf00000-dbffffff
Prefetchable memory behind bridge: 0000000088000000-00000000880fffff
Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
Subsystem: ASUSTeK Computer Inc. Device 8179
Flags: bus master, medium devsel, latency 0
Capabilities: <access denied>
Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
Subsystem: ASUSTeK Computer Inc. Device 8179
Flags: bus master, medium devsel, latency 0, IRQ 22
I/O ports at 01f0 [size=8]
I/O ports at 03f4 [size=1]
I/O ports at 0170 [size=8]
I/O ports at 0374 [size=1]
I/O ports at ffa0 [size=16]
Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
Subsystem: ASUSTeK Computer Inc. Device 2601
Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 23
I/O ports at c800 [size=8]
I/O ports at c400 [size=4]
I/O ports at c000 [size=8]
I/O ports at b800 [size=4]
I/O ports at b400 [size=16]
Capabilities: <access denied>
Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
Subsystem: ASUSTeK Computer Inc. Device 8179
Flags: medium devsel, IRQ 5
I/O ports at 0400 [size=32]
Kernel modules: i2c-i801

01:01.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
Subsystem: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 21
Memory at dbfe0000 (32-bit, non-prefetchable) [size=64K]
Memory at dbfb0000 (32-bit, non-prefetchable) [size=64K]
Capabilities: <access denied>
Kernel driver in use: ndiswrapper

01:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)
Subsystem: ASUSTeK Computer Inc. Device 811a
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
Memory at dbffc000 (32-bit, non-prefetchable) [size=16K]
I/O ports at d800 [size=256]
Expansion ROM at 88000000 [disabled] [size=128K]
Capabilities: <access denied>
Kernel driver in use: skge
Kernel modules: skge

02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
Subsystem: ASUSTeK Computer Inc. Device 8266
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at df000000 (32-bit, non-prefetchable) [size=16M]
Memory at e0000000 (64-bit, prefetchable) [size=256M]
Memory at dc000000 (64-bit, non-prefetchable) [size=32M]
I/O ports at e800 [size=128]
[virtual] Expansion ROM at defe0000 [disabled] [size=128K]
Capabilities: <access denied>
Kernel driver in use: nvidia
Kernel modules: nvidia, nvidiafb

Any help would be appreciated. Ubuntu is all that I use but getting the kids to use it when it does not want to log on to our router is a big deterent for them.

Ron

---

### Post by PostWax on 2009-06-13
Bump

Can anyone offer some advice?

---

