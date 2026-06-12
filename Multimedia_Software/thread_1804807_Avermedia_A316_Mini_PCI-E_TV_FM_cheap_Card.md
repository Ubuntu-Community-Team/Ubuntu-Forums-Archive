---
title: "Avermedia A316 Mini PCI-E TV FM cheap Card"
date: 2011-07-15
forum: Multimedia Software
---

### Post by luismidelgado on 2011-07-15
Hi

I bought this card on ebay [[http://cgi.ebay.es/ws/eBayISAPI.dll?ViewItem&item=180559590269&ssPageName=STRK:MEWNX:IT]](http://cgi.ebay.es/ws/eBayISAPI.dll?ViewItem&item=180559590269&ssPageName=STRK:MEWNX:IT]), thinking it was compatible with linux. What I get in Ubuntu 11.04 is:

lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)

lspci -vn
00:00.0 0600: 10de:0a82 (rev b1)
	Subsystem: 10de:cb79
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 0500: 10de:0a88 (rev b1)
	Subsystem: 10de:cb79
	Flags: bus master, 66MHz, fast devsel, latency 0

00:03.0 0601: 10de:0aad (rev b2)
	Subsystem: 19da:a119
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 4f00 [size=256]

00:03.1 0500: 10de:0aa4 (rev b1)
	Subsystem: 19da:a119
	Flags: 66MHz, fast devsel

00:03.2 0c05: 10de:0aa2 (rev b1)
	Subsystem: 19da:a119
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at 4900 [size=64]
	I/O ports at 4d00 [size=64]
	I/O ports at 4e00 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:03.3 0500: 10de:0a89 (rev b1)
	Subsystem: 10de:cb79
	Flags: 66MHz, fast devsel

00:03.5 0b40: 10de:0aa3 (rev b1)
	Subsystem: 19da:a119
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fae80000 (32-bit, non-prefetchable) [size=512K]
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current

00:04.0 0c03: 10de:0aa5 (rev b1) (prog-if 10 [OHCI])
	Subsystem: 19da:a119
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fae7f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:04.1 0c03: 10de:0aa6 (rev b1) (prog-if 20 [EHCI])
	Subsystem: 19da:a119
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fae7ec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:06.0 0c03: 10de:0aa7 (rev b1) (prog-if 10 [OHCI])
	Subsystem: 19da:a119
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fae7d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:06.1 0c03: 10de:0aa9 (rev b1) (prog-if 20 [EHCI])
	Subsystem: 19da:a119
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fae7e800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:08.0 0403: 10de:0ac0 (rev b1)
	Subsystem: 174b:437b
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fae78000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:09.0 0604: 10de:0aab (rev b1) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Capabilities: <access denied>

00:0a.0 0200: 10de:0ab0 (rev b1)
	Subsystem: 19da:a119
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fae7c000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at d080 [size=8]
	Memory at fae7e400 (32-bit, non-prefetchable) [size=256]
	Memory at fae7e000 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:0b.0 0101: 10de:0ab4 (rev b1) (prog-if 85 [Master SecO PriO])
	Subsystem: 19da:a119
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 40
	I/O ports at d000 [size=8]
	I/O ports at cc00 [size=4]
	I/O ports at c880 [size=8]
	I/O ports at c800 [size=4]
	I/O ports at c480 [size=16]
	Memory at fae76000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:0c.0 0604: 10de:0ac4 (rev b1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:10.0 0604: 10de:0aa0 (rev b1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: faf00000-fbffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000f9ffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:15.0 0604: 10de:0ac6 (rev b1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.0 0604: 10de:0ac7 (rev b1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:17.0 0604: 10de:0ac7 (rev b1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:18.0 0604: 10de:0ac7 (rev b1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

03:00.0 0300: 10de:087d (rev b1) (prog-if 00 [VGA controller])
	Subsystem: 19da:a119
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f8000000 (64-bit, prefetchable) [size=32M]
	I/O ports at ec00 [size=128]
	[virtual] Expansion ROM at fafe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nouveau, nvidiafb

and dmesg is an attachment.

If this card does not work, there are some cheap PCIe mini card that works in linux?

Thank you all.

---

