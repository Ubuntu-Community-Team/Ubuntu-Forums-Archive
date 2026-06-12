---
title: "Considering Switching Internal Wireless Adapter"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by tdrusk on 2011-03-28
Hey guys, 
I am hoping to get a wireless router that will work fully in GNU/Linux. I have a Toshiba Satellite L655D-S5093. My current wireless card is giving me trouble and I would prefer one that can be installed out-of-the-box with open-source drivers. I want to take out my current card and replace it with the new, better one. 

I really don't know much about wireless cards and wouldn't know the right connection(if there even is one). All I know is that my card is internal and it needs to come out!

Just to answer more questions: My current driver is causing my system to have mini-freezes. I am using the rtl8192ce driver. This is my lspci:

```
$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
	Subsystem: Toshiba America Info Systems Device fd50
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Toshiba America Info Systems Device 9602 (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: d4100000-d42fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
	I/O behind bridge: 00007000-0000afff
	Memory behind bridge: d3100000-d40fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: d3000000-d30fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
	Subsystem: Toshiba America Info Systems Device fd50
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	I/O ports at c038 [size=8]
	I/O ports at c04c [size=4]
	I/O ports at c030 [size=8]
	I/O ports at c048 [size=4]
	I/O ports at c010 [size=16]
	Memory at d4307000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Device fd50
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d4306000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Device fd50
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at d4307600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Device fd50
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d4305000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Device fd50
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at d4307500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
	Subsystem: Toshiba America Info Systems Device fd50
	Flags: 66MHz, medium devsel
	Kernel driver in use: piix4_smbus

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
	Subsystem: Toshiba America Info Systems Device fd50
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at d4300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
	Subsystem: Toshiba America Info Systems Device fd50
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=64

00:15.0 PCI bridge: ATI Technologies Inc Device 43a0 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0f, sec-latency=0
	I/O behind bridge: 00002000-00005fff
	Memory behind bridge: d2000000-d2ffffff
	Prefetchable memory behind bridge: 00000000d1000000-00000000d1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport

00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Device fd50
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d4304000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Device fd50
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at d4307400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
	Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200] (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Device fd50
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at b000 [size=256]
	Memory at d4200000 (32-bit, non-prefetchable) [size=64K]
	Memory at d4100000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: radeon

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device 8185
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at 7000 [size=256]
	Memory at d3100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: rtl8192CE

08:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
	Subsystem: Toshiba America Info Systems Device fd50
	Flags: bus master, fast devsel, latency 0, IRQ 27
	Memory at d3000000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 6000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: atl1c


```

Thanks in advance!

---

### Post by tdrusk on 2011-04-02
I went ahead and ordered[ this]("http://www.amazon.com/gp/product/B0036BJN12") card. According to the ubuntu wiki it works out of the box, is better than my current card, and works better in noisy environments(I think this is my real problem). Will post back later if it works well.

---

