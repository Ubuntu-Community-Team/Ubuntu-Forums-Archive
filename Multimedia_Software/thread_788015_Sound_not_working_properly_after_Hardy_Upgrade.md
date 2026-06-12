---
title: "Sound not working properly after Hardy Upgrade"
date: 2008-05-09
forum: Multimedia Software
---

### Post by ashkev on 2008-05-09
I have not been able to get sound to work properly on my Gateway MX6453 Laptop after a recent upgrade to Hardy.  When I go to system>Preferences>Sound and click on autodetect sound, I get a clicking sound.  If I change it to OSS, I hear the test sound, but I still can't hear anything such as login or logout sounds, or any sound in firefox java, or Amarok.  Output of aplay -l is:

kevin@kevin-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Output of lspci -v is:

kevin@kevin-laptop:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
	Subsystem: Gateway 2000 Unknown device 0367
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: c0100000-c01fffff
	Prefetchable memory behind bridge: 00000000c8000000-00000000cfffffff
	Capabilities: <access denied>

00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: c0200000-c02fffff
	Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
	Memory behind bridge: c0300000-c03fffff
	Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Gateway 2000 Unknown device 0367
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at c0004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Gateway 2000 Unknown device 0367
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at c0005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
	Subsystem: Gateway 2000 Unknown device 0367
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at c0006000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
	Subsystem: Gateway 2000 Unknown device 0367
	Flags: 66MHz, medium devsel
	I/O ports at 8400 [size=16]
	Memory at fed00000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 82 [Master PriP])
	Subsystem: Gateway 2000 Unknown device 0367
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8410 [size=16]
	Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
	Subsystem: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller
	Flags: bus master, slow devsel, latency 64, IRQ 19
	Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
	Subsystem: Gateway 2000 Unknown device 0367
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=08, subordinate=0b, sec-latency=64
	Memory behind bridge: c0400000-c04fffff

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

01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] (prog-if 00 [VGA controller])
	Subsystem: Gateway 2000 Unknown device 0367
	Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 17
	Memory at c8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 9000 [size=256]
	Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c0120000 [disabled] [size=128K]
	Capabilities: <access denied>

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
	Subsystem: Gateway 2000 Unknown device 0367
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at c0200000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at a000 [size=256]
	Capabilities: <access denied>

05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
	Subsystem: Broadcom Corporation Unknown device 0465
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at c0300000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

08:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Gateway 2000 Unknown device 0367
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at c0404000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=08, secondary=09, subordinate=0a, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 8c000000-8ffff000
	I/O window 0: 00001400-000014ff
	I/O window 1: 00001800-000018ff
	16-bit legacy interface ports at 0001

08:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
	Subsystem: Gateway 2000 Unknown device 0367
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at c0405000 (32-bit, non-prefetchable) [size=2K]
	Memory at c0400000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

08:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Gateway 2000 Unknown device 0367
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at c0406000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

I am not sure where to go from here...

Any advice would be appreciated.

---

### Post by confy on 2008-05-09
I have simular problem after upgrading...
I usualy use ALSA drivers so i can handle but everything when that i mark "autodetect" they don't detect...
This is my 
confy@live:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
confy@live:~$

In totem i can't choice what drivers to choice so it blocks...

---

### Post by confy on 2008-05-09
ok... i fixed by typing "gstreamer-properties" and choosing  ALSA...
Hope it will help :)

---

### Post by ashkev on 2008-05-09
Thanks, but that didn't do it.... I also tried OSS and when I hit TEST, I hear the test sound, but that's it.  When I try to play AMarok, for instance, I just here crackly speaker sounds....

---

### Post by Mr_Arne on 2008-05-10
I'm sitting with an ATI-equipped computer (for me a new experience..) and I believe this has to do with bad behavior from the ATI driver. I've been switching a couple of times between Gutsy and Hardy the last days on this machine, and I noticed this when wrestling with Gutsy. I am about to start investigation for Hardy now, but I don't now where to start. The issue doesn't seem so highlighted earlier...

Regards

Ola

---

### Post by confy on 2008-05-14
perhaps this can help:
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

