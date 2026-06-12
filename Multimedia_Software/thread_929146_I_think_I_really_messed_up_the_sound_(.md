---
title: "I think I really messed up the sound :("
date: 2008-09-24
forum: Multimedia Software
---

### Post by A-sop on 2008-09-24
I'm really sorry to bother you with this, but it's late, I've been at this for two days now and I think I've done more harm than good!

I have no sound. it all started when I wanted to use Skype. After spending hours trying to get it to work again, using the right combination of where to actually plug-in the headset and which settings to choose.

Then my sound went. I have already read and followed the threads here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

here:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) 

here:

[http://ubuntuforums.org/showthread.php?t=730378&highlight=Audio+output+unavailable%3B+device+busy.+xine+parameters%3A](http://ubuntuforums.org/showthread.php?t=730378&highlight=Audio+output+unavailable%3B+device+busy.+xine+parameters%3A)

and here:

[http://ubuntuforums.org/showthread.php?t=729333&highlight=intel+hda](http://ubuntuforums.org/showthread.php?t=729333&highlight=intel+hda)

I would love to provide you with info, but I don't really know where to bring that all up from, this is all I know:

```
logan@logan:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7050 PV / nForce 630a (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

```

```
logan@logan:~$ lspci -v
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
	Subsystem: Elitegroup Computer Systems Unknown device 2609
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
	Subsystem: Elitegroup Computer Systems Unknown device 2609
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 2f00 [size=256]

00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
	Subsystem: Elitegroup Computer Systems Unknown device 2609
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at ec00 [size=64]
	I/O ports at 2d00 [size=64]
	I/O ports at 2e00 [size=64]
	Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10 [OHCI])
	Subsystem: Elitegroup Computer Systems Unknown device 2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at febff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20 [EHCI])
	Subsystem: Elitegroup Computer Systems Unknown device 2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at febfec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10 [OHCI])
	Subsystem: Elitegroup Computer Systems Unknown device 2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at febfd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20 [EHCI])
	Subsystem: Elitegroup Computer Systems Unknown device 2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	Memory at febfe800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f019:2609
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: <access denied>

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
	Subsystem: Elitegroup Computer Systems Unknown device 2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	Memory at febf8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Elitegroup Computer Systems Unknown device 2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	I/O ports at e480 [size=8]
	I/O ports at e400 [size=4]
	I/O ports at e080 [size=8]
	I/O ports at e000 [size=4]
	I/O ports at dc00 [size=16]
	Memory at febf6000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
	Subsystem: Elitegroup Computer Systems Unknown device 2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 216
	Memory at febfc000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at d880 [size=8]
	Memory at febfe400 (32-bit, non-prefetchable) [size=256]
	Memory at febfe000 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>

00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Capabilities: <access denied>

00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Capabilities: <access denied>

00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Capabilities: <access denied>

00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Capabilities: <access denied>

00:12.0 VGA compatible controller: nVidia Corporation GeForce 7050 PV / nForce 630a (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Elitegroup Computer Systems Unknown device 2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at febc0000 [disabled] [size=128K]
	Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

```

are there any other things I need to give you so you can help me?

I am truly clueless! Any help would really be appreciated.

A-sop

---

