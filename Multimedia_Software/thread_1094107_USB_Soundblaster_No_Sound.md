---
title: "USB Soundblaster No Sound"
date: 2009-03-12
forum: Multimedia Software
---

### Post by JerryI on 2009-03-12
My USB Soundblaster works in Vista.  Not in dual boot Ubuntu.  My linux experience level is now about 4 days of glacial progress.  Got Ubuntu 10.8 running last night for first time.  Got my dual-monitors working.  No sound from my USB Soundblaster in Ubuntu. I read somewhere to start by typing lspci -v and got the following, which I think indicates no sound driver for Soundblaster.  But then I got lost when it said go to some link that was way over my head.  I don't know how to make files and edit and compile and all that kind of geek stuff yet.  Pls give me an idea what to do next.  It's been about four days of around-the-clock work to get this far.  I don't think that getting sound out of a widely marketed card should be a Manhattan Project, especially if it even works in Vista.

---------------------------------------------------------

gai@ubuntu:~$ dir
Desktop    Dual\ Monitor\ Hints  Music	   Public     Videos
Documents  Examples		 Pictures  Templates
gai@ubuntu:~$ lspci -v
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a54
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a54
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a54
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a54
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a54
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a54
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a54
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a54
	Flags: 66MHz, fast devsel

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f8000000-fbffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a54
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
	Subsystem: Hewlett-Packard Company Device 2a54
	Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
	Subsystem: Hewlett-Packard Company Device 2a54
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at 4c00 [size=64]
	I/O ports at 4c40 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
	Subsystem: Hewlett-Packard Company Device 2a54
	Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 2a54
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 2a54
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Device 2a54
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at e400 [size=16]
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv, pata_acpi, ata_generic

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Device 2a38
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at d000 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv, pata_acpi, ata_generic

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: fdd00000-fddfffff
	Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: Hewlett-Packard Company Device 2a54
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
	Subsystem: Hewlett-Packard Company Device 2a54
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at cc00 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: isp1760, forcedeth

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
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
	Subsystem: XFX Pine Group Inc. Device 2309
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at ac00 [size=128]
	[virtual] Expansion ROM at fbfe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

02:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 2a54
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at fdeff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

---

### Post by JerryI on 2009-03-12
BTW, aplay -l yields the following, I think this means I need to find and install the driver for the External [SB..............

Pls let me know if that is so, and how.

----------------------------

gai@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: External [SB Live! 24-bit External], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
gai@ubuntu:~$

---

### Post by markbuntu on 2009-03-12
no need to find a driver since aplay reports the card just fine. If you want to use it along with you on-board sound go here

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

