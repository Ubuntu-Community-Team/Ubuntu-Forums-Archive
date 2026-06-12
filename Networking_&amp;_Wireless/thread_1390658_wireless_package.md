---
title: "wireless package"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by jtmedin on 2010-01-25
Have a pci wireless card from airlink but unable to find the drivers for it. About all the info on the card is that its a g card. Ran lspci & got 'ab9com system inc' with a 'ab90' also. So what can i do to find the drivers. I also was looking for a wireless package for getting wireless on the air. I cant remember the name. Anyone got any ideas on either of these problems? TIA

---

### Post by pdc on 2010-01-25
I suspect there will be more information from 

> lspci

than you have chosen to give the forum;

[I]eg here is advice from another forum 
[/I]
> (b) [I]If it is a PCI device, you should enter the command '**lspci**' in a terminal. The output will look like:

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
[/I]
.... snip ...

[I]01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
**04:00.0** Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

A recent computer will have lots of connections to the PCI bus, which is why I snipped out a number of entries from my machine. The PCI wireless device here is the BCM4312. . For PCI, the above list does not provide all the information. [/I]

Next, you should enter the command '**lspci -n**'. The list will be equally long and look like:

[I]00:00.0 0500: 10de:0547 (rev a2)
00:01.0 0601: 10de:0548 (rev a2)

-- snip --

01:09.4 0880: 1180:0852 (rev 12)[/I]
**04:00.0** 0280: 14e4:4312 (rev 01)

At this point, 

you need to match the bus number (the numbers at the front that look like **04:00.0**) from the first list to the second. 

**_These are the PCI vendor and product ID codes._** 

[I]For my BCM4312, these data are 14e4:4312. [B][U]When you post a
request for help, include both lines[/U][/B][/I].

He is talking about a broadcom device, but you can hopefully see the principle

---

### Post by jtmedin on 2010-01-26
Ok here is the lspci:

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
	Subsystem: ABIT Computer Corp. Device 1015
	Flags: bus master, fast devsel, latency 0
	Memory at f0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Memory behind bridge: f4000000-f6ffffff
	Prefetchable memory behind bridge: e0000000-efffffff
	Kernel modules: shpchp

00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
	Flags: fast devsel
	Memory at fecf0000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
	Subsystem: ABIT Computer Corp. Device 1015
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at bc00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
	Subsystem: ABIT Computer Corp. Device 1015
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at b000 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
	Subsystem: ABIT Computer Corp. Device 1015
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at b400 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
	Subsystem: ABIT Computer Corp. Device 1015
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at b800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: ABIT Computer Corp. Device 1015
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f7100000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f7000000-f70fffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: ABIT Computer Corp. Device 1015
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f000 [size=16]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
	Subsystem: ABIT Computer Corp. Device 1015
	Flags: medium devsel, IRQ 11
	I/O ports at 0500 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6800 GS] (rev a2)
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 248, IRQ 16
	Memory at f4000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at f6000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

02:02.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)
	Subsystem: ABIT Computer Corp. Device 100b
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at f7020000 (32-bit, non-prefetchable) [size=16K]
	I/O ports at a000 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: skge
	Kernel modules: skge

02:04.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
	Subsystem: Abocom Systems Inc Device ab90
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at f7024000 (32-bit, non-prefetchable) [size=8K]
	Memory at f7000000 (32-bit, non-prefetchable) [size=128K]
	Capabilities: <access denied>

---

### Post by jtmedin on 2010-01-26
bump:  Still looking for the wireless package

---

### Post by jtmedin on 2010-01-27
Bump: Ok so what does this help to find the drivers? TIA

---

