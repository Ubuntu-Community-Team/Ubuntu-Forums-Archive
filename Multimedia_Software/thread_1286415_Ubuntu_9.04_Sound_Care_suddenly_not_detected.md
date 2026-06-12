---
title: "Ubuntu 9.04 Sound Care suddenly not detected"
date: 2009-10-08
forum: Multimedia Software
---

### Post by HobbDogg on 2009-10-08
I don't know what happened. As of two days ago i have no sound. I used to have sound so my only thoughts is that it was an update that killed the audio. Here is what i have tried:

```
aplay -l
aplay: device_list:217: no soundcards found...

```

```
lspci -v
00:00.0 Host bridge: nVidia Corporation MCP73 Host Bridge (rev a2)
	Subsystem: nVidia Corporation Device cb73
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
	Subsystem: nVidia Corporation Device cb73
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: nVidia Corporation Device cb73
	Flags: 66MHz, fast devsel

00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: nVidia Corporation Device cb73
	Flags: 66MHz, fast devsel

00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: nVidia Corporation Device cb73
	Flags: 66MHz, fast devsel

00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: nVidia Corporation Device cb73
	Flags: 66MHz, fast devsel

00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: nVidia Corporation Device cb73
	Flags: 66MHz, fast devsel

00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: nVidia Corporation Device cb73
	Flags: 66MHz, fast devsel

00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: nVidia Corporation Device cb73
	Flags: 66MHz, fast devsel

00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
	Subsystem: nVidia Corporation Device cb73
	Flags: 66MHz, fast devsel

00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
	Subsystem: Giga-byte Technology Device 5001
	Flags: bus master, 66MHz, fast devsel, latency 0

00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
	Subsystem: Giga-byte Technology Device 07d8
	Flags: 66MHz, fast devsel, IRQ 5
	I/O ports at c800 [size=64]
	I/O ports at 1c00 [size=64]
	I/O ports at 1c80 [size=64]
	Capabilities: <access denied>

00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Device cb73
	Flags: 66MHz, fast devsel

00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Device cb73
	Flags: 66MHz, fast devsel

00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1) (prog-if 10)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at e6107000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1) (prog-if 20)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at e6106000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Device f458:b000
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd

00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
	Memory at e6100000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Memory behind bridge: e6000000-e60fffff
	Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: e0000000-e3ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0e.0 IDE interface: nVidia Corporation MCP73 IDE (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology Device b002
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2302
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at dc00 [size=16]
	Memory at e6104000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
	Subsystem: Giga-byte Technology Device e000
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2301
	Memory at e6108000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at e000 [size=8]
	Memory at e6109000 (32-bit, non-prefetchable) [size=256]
	Memory at e610a000 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

01:06.0 Network controller: RaLink RT2800 802.11n PCI
	Subsystem: RaLink Device 2860
	Flags: bus master, slow devsel, latency 32, IRQ 17
	Memory at e6000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: rt2860
	Kernel modules: rt2860sta

01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: Giga-byte Technology Device 1000
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at e6014000 (32-bit, non-prefetchable) [size=2K]
	Memory at e6010000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

02:00.0 VGA compatible controller: nVidia Corporation GeForce 9600 GSO (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 82cb
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at e2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at e0000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at b000 [size=128]
	[virtual] Expansion ROM at e3000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb


```

Also when i open up the sound Volume Control this is Displayed: Playback: Null Output (PulseAudio Mixer). When i open System>Preferences>Sound the main value(that used to be correct) is: HDA NVidia NVIDIA HDMI (ALSA) (Not Connected). None of the tests produce sound at all from any of the devices in the drop down menu. Any help on this matter would be much appreciated. Thanks in advanced

---

### Post by HobbDogg on 2009-10-09
SOLVED: used this website: [http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)

---

