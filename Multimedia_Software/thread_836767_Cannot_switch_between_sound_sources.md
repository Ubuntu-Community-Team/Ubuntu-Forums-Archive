---
title: "Cannot switch between sound sources"
date: 2008-06-21
forum: Multimedia Software
---

### Post by VoiceOvGod on 2008-06-21
Hi!

I just upgraded from 7.10 to 8.04.

I am encountering an interesting issue with my sound:

1 - listening to an audio CD.
2 - Attempt to switch to a video in my browser (YouTube, etc), video will play, but sound will not.
3 - Attempt to listen to Audio File - no playback.

The only way I can get playback again is if I log out and then back in again.

Specs for aplay and lspci below:

```

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
 lspci -v
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
	Subsystem: Unknown device cb84:10de
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
	Subsystem: Unknown device cb84:10de
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
	Subsystem: Unknown device cb84:10de
	Flags: 66MHz, fast devsel, IRQ 5
	I/O ports at fc00 [size=32]
	I/O ports at f800 [size=64]
	I/O ports at f400 [size=64]
	Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
	Subsystem: Unknown device cb84:10de
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at febff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: Unknown device cb84:10de
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at feb00000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
	Subsystem: Chaintech Computer Co. Ltd Unknown device f647
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	I/O ports at f000 [size=256]
	I/O ports at ec00 [size=256]
	Memory at febfd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device fb84:10de
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at e000 [size=16]
	Capabilities: <access denied>

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
	Subsystem: Unknown device cb84:10de
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at cc00 [size=16]
	Memory at febfb000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
	Subsystem: Unknown device cb84:10de
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at b800 [size=16]
	Memory at febfa000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fe900000-fe9fffff
	Prefetchable memory behind bridge: fea00000-feafffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
	Subsystem: Unknown device cb84:10de
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at febf9000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at b400 [size=8]
	Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fe800000-fe8fffff
	Prefetchable memory behind bridge: 00000000fe700000-00000000fe7fffff
	Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: fe600000-fe6fffff
	Prefetchable memory behind bridge: 00000000fe500000-00000000fe5fffff
	Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: fe400000-fe4fffff
	Prefetchable memory behind bridge: 00000000fe300000-00000000fe3fffff
	Capabilities: <access denied>

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: f4000000-fbffffff
	Prefetchable memory behind bridge: 00000000d8000000-00000000dfffffff
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

05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Unknown device 81a4
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at f4000000 (32-bit, non-prefetchable) [size=64M]
	Memory at d8000000 (64-bit, prefetchable) [size=128M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at f8000000 [disabled] [size=128K]
	Capabilities: <access denied>

```

---

### Post by VoiceOvGod on 2008-06-21
Interesting.

I switched from Movie Player to Rhythmbox, and encountered no problems. But switching from either to web or cd again is a no-go.

---

### Post by mc4man on 2008-06-22
You may want to read thru here to see if it's the same issue, seems similar [http://ubuntuforums.org/showthread.php?t=836596](http://ubuntuforums.org/showthread.php?t=836596)

---

### Post by Soo on 2008-06-22
I have a similar issue only the libflashsupport fix doesn't do it for me. I can have say Firefox and VLC producing sound at the same time, but nothing in conjunction with mpd. (8.04)

---

