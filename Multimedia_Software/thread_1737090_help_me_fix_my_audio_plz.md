---
title: "help me fix my audio plz"
date: 2011-04-23
forum: Multimedia Software
---

### Post by Bluestars on 2011-04-23
I couldn't get audio to work in Dragon Age 2, and someone told me to uninstall pulseaudio, and install OSS4. I followed this guide [http://ubuntuforums.org/showthread.php?t=1610680&page=2](http://ubuntuforums.org/showthread.php?t=1610680&page=2).

It didn't work so I uninstalled OSS, reinstalled pulse audio but when I reboot now I intially have audio. After a little while of use my audio stops working until I reboot again. Can anyone help me plz?

---

### Post by fdrake on 2011-04-23
on the shell try:
aplay -l
   and 
lspci -v

post their output please.

---

### Post by Bluestars on 2011-04-23
> **fdrake said:**
> on the shell try:
aplay -l
   and 
lspci -v

post their output please.

Hmm, it seems like audio only stops working after I try to launch a game.  Fall Out New Vegas tells me no audio device detected and then I get non audio system wide afterwards.

aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```



lspci -v
```
00:00.0 Host bridge: nVidia Corporation Device 0802 (rev b1)
	Subsystem: eVga.com. Corp. Device 1004
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation Device 0808 (rev a1)
	Subsystem: eVga.com. Corp. Device 1004
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation Device 0809 (rev a1)
	Subsystem: eVga.com. Corp. Device 1004
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation Device 080a (rev a1)
	Subsystem: eVga.com. Corp. Device 1004
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.4 RAM memory: nVidia Corporation Device 080b (rev a1)
	Subsystem: eVga.com. Corp. Device 1004
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation Device 080c (rev b1)
	Subsystem: eVga.com. Corp. Device 1004
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.6 RAM memory: nVidia Corporation Device 080d (rev a1)
	Subsystem: eVga.com. Corp. Device 1004
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation Device 080e (rev a1)
	Subsystem: eVga.com. Corp. Device 1004
	Flags: 66MHz, fast devsel

00:01.0 RAM memory: nVidia Corporation Device 080f (rev a1)
	Subsystem: eVga.com. Corp. Device 1004
	Flags: 66MHz, fast devsel

00:01.1 RAM memory: nVidia Corporation Device 0810 (rev a1)
	Subsystem: eVga.com. Corp. Device 1004
	Flags: 66MHz, fast devsel

00:01.2 RAM memory: nVidia Corporation Device 0811 (rev a1)
	Subsystem: eVga.com. Corp. Device 1004
	Flags: 66MHz, fast devsel

00:01.3 RAM memory: nVidia Corporation Device 0812 (rev a1)
	Subsystem: eVga.com. Corp. Device 1004
	Flags: 66MHz, fast devsel

00:01.4 RAM memory: nVidia Corporation Device 0813 (rev a1)
	Subsystem: eVga.com. Corp. Device 1004
	Flags: 66MHz, fast devsel

00:01.5 RAM memory: nVidia Corporation Device 0814 (rev a1)
	Subsystem: eVga.com. Corp. Device 1004
	Flags: 66MHz, fast devsel

00:01.6 RAM memory: nVidia Corporation Device 081a (rev a1)
	Subsystem: eVga.com. Corp. Device 1004
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.7 RAM memory: nVidia Corporation Device 080e (rev a1)
	Subsystem: eVga.com. Corp. Device 1004
	Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation Device 0815 (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: c6000000-c9ffffff
	Prefetchable memory behind bridge: 00000000a0000000-00000000afffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:04.0 PCI bridge: nVidia Corporation Device 0817 (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: ca000000-cdffffff
	Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
	Subsystem: eVga.com. Corp. Device 1004
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
	Subsystem: eVga.com. Corp. Device 1004
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at fc00 [size=128]

00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
	Subsystem: eVga.com. Corp. Device 1004
	Flags: 66MHz, fast devsel, IRQ 255
	I/O ports at f800 [size=64]
	I/O ports at f400 [size=64]
	I/O ports at f000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1) (prog-if 10 [OHCI])
	Subsystem: eVga.com. Corp. Device 1004
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at cffff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2) (prog-if 20 [EHCI])
	Subsystem: eVga.com. Corp. Device 1004
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at cfffe000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: eVga.com. Corp. Device 1004
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at ec00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
	Subsystem: eVga.com. Corp. Device 1004
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at d800 [size=16]
	Memory at cfffd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
	Subsystem: eVga.com. Corp. Device 1004
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at c400 [size=16]
	Memory at cfffc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
	Subsystem: eVga.com. Corp. Device 1004
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	I/O ports at c000 [size=8]
	I/O ports at bc00 [size=4]
	I/O ports at b800 [size=8]
	I/O ports at b400 [size=4]
	I/O ports at b000 [size=16]
	Memory at cfffb000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Memory behind bridge: cfe00000-cfefffff
	Capabilities: <access denied>

00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
	Subsystem: eVga.com. Corp. Device 1004
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at cfff0000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
	Subsystem: eVga.com. Corp. Device 1004
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 44
	Memory at cfffa000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ac00 [size=8]
	Memory at cfff9000 (32-bit, non-prefetchable) [size=256]
	Memory at cfff8000 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
	Subsystem: eVga.com. Corp. Device 1004
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 45
	Memory at cfff7000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at a800 [size=8]
	Memory at cfff6000 (32-bit, non-prefetchable) [size=256]
	Memory at cfff5000 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:14.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00006000-00007fff
	Memory behind bridge: cfd00000-cfdfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:15.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00005fff
	Memory behind bridge: cfc00000-cfcfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

01:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 260] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: eVga.com. Corp. Device 1265
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at c8000000 (32-bit, non-prefetchable) [size=16M]
	Memory at a0000000 (64-bit, prefetchable) [size=256M]
	Memory at c6000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 9c00 [size=128]
	[virtual] Expansion ROM at c9000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nouveau, nvidiafb

02:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 260] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: eVga.com. Corp. Device 1265
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at cc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Memory at ca000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 8c00 [size=128]
	[virtual] Expansion ROM at cd000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nouveau, nvidiafb

03:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
	Subsystem: nVidia Corporation Device c73e
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at cfeff000 (32-bit, non-prefetchable) [size=2K]
	Memory at cfef8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci, ohci1394

04:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: nVidia Corporation Device 0156
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at cfdfe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

04:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03) (prog-if 85 [Master SecO PriO])
	Subsystem: nVidia Corporation Device 0156
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at 7c00 [size=8]
	I/O ports at 7800 [size=4]
	I/O ports at 7400 [size=8]
	I/O ports at 7000 [size=4]
	I/O ports at 6c00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_jmicron
	Kernel modules: pata_jmicron

05:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: nVidia Corporation Device 0156
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at cfcfe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

05:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03) (prog-if 85 [Master SecO PriO])
	Subsystem: nVidia Corporation Device 0156
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at 5c00 [size=8]
	I/O ports at 5800 [size=4]
	I/O ports at 5400 [size=8]
	I/O ports at 5000 [size=4]
	I/O ports at 4c00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_jmicron
	Kernel modules: pata_jmicron

anon@anon-132-YW-E180-FTW:~$ 

```

---

