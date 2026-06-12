---
title: "Help whit sound"
date: 2008-09-29
forum: Multimedia Software
---

### Post by steffenomak on 2008-09-29
Hi!
I have had the earlier version of ubuntu and sound was working. But now i got 8.04 and i don't have sound. I tried the Comprehensive Sound Problem Solutions Guide v0.5e and after the first step I was successfull and whent down to the alsamixer sektion where I found nothing to be muted. Tried diffrent things but nothing worked for me.

> 00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: 66MHz, fast devsel

00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: 66MHz, fast devsel

00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: 66MHz, fast devsel

00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: 66MHz, fast devsel

00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: 66MHz, fast devsel

00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: 66MHz, fast devsel

00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: 66MHz, fast devsel

00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: 66MHz, fast devsel

00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: 66MHz, fast devsel

00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: bus master, 66MHz, fast devsel, latency 0

00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: 66MHz, fast devsel

00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: ca000000-cdffffff
	Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
	Capabilities: <access denied>

00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at fc00 [size=128]

00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: 66MHz, fast devsel, IRQ 255
	I/O ports at f800 [size=64]
	I/O ports at f400 [size=64]
	I/O ports at f000 [size=64]
	Capabilities: <access denied>

00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1) (prog-if 10 [OHCI])
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at cffff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2) (prog-if 20 [EHCI])
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at cfffe000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f0de:c55e
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ec00 [size=16]
	Capabilities: <access denied>

00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at d800 [size=16]
	Memory at cfffd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at c400 [size=16]
	Memory at cfffc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	I/O ports at c000 [size=8]
	I/O ports at bc00 [size=4]
	I/O ports at b800 [size=8]
	I/O ports at b400 [size=4]
	I/O ports at b000 [size=16]
	Memory at cfffb000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: cfd00000-cfdfffff
	Prefetchable memory behind bridge: cfe00000-cfefffff
	Capabilities: <access denied>

00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at cfff0000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 222
	Memory at cfff7000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at a800 [size=8]
	Memory at cfff6000 (32-bit, non-prefetchable) [size=256]
	Memory at cfff5000 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: XFX Pine Group Inc. Unknown device 2252
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at cc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Memory at ca000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 9c00 [size=128]
	[virtual] Expansion ROM at cd000000 [disabled] [size=128K]
	Capabilities: <access denied>

02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
	Subsystem: nVidia Corporation Unknown device c55e
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at cfdff000 (32-bit, non-prefetchable) [size=2K]
	Memory at cfdf8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>


> kort 0: NVidia [HDA NVidia], enhet 0: ALC882 Analog [ALC882 Analog]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 0: NVidia [HDA NVidia], enhet 1: ALC882 Digital [ALC882 Digital]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0



pleas could someone help me.

---

### Post by markbuntu on 2008-09-29
There is some help for configuring for the ALC882 here:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

There is also a bug report about scratchy sound with the Nvidia HDA sound chips which may or may not effect you. It is fixed in the 2.6.27 kernel which will be avaiable with Intrepid at the end of October.

---

### Post by steffenomak on 2008-09-30
ok thanks for the help but on that thread it doesn't say where to add thous lines.

> ALC882/885
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack digital with SPDIF I/O
arima Arima W820Di1
targa Targa T8, MSI-1049 T8
asus-a7j ASUS A7J
asus-a7m ASUS A7M
macpro MacPro support
mbp3 Macbook Pro rev3
imac24 iMac 24'' with jack detection
w2jc ASUS W2JC
auto auto-config reading BIOS (default)


where should thous lines go in to:
> # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388


---

