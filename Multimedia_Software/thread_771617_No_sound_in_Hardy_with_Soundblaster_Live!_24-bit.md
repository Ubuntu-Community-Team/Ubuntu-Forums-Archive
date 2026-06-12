---
title: "No sound in Hardy with Soundblaster Live! 24-bit"
date: 2008-04-27
forum: Multimedia Software
---

### Post by IgnacioMiller on 2008-04-27
Hey all,

I just did a fresh install of Ubuntu 8.04 (64-bit) on my computer. Everything works save for the sound on my system. I changed the device to my soundcard, a Soundblaster Live! 24 bit, but it still had no playback. I then selected every track/channel and unmuted/raised the volume on each one. I turned the IEC958 switch on too. I also went into alsamixer, selected my card and tried to see if there were any channels still muted and there were not. I have noticed that upon reaching the login screen, the three drumbeats do play but no further sounds will player after logging in. This lead me to believe that I didn't have permission to use audio, but I checked and I do.

Here is my output of lspci -v:
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: <access denied>

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fa900000-fe9fffff
	Prefetchable memory behind bridge: 00000000bff00000-00000000dfefffff
	Capabilities: <access denied>

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: 66MHz, fast devsel, IRQ 5
	I/O ports at 0600 [size=64]
	I/O ports at 0700 [size=64]
	Capabilities: <access denied>

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at febbe000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at febbfc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f043:81bc
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: <access denied>

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	I/O ports at e800 [size=8]
	I/O ports at e480 [size=4]
	I/O ports at e400 [size=8]
	I/O ports at e080 [size=4]
	I/O ports at e000 [size=16]
	Memory at febbd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at dc00 [size=8]
	I/O ports at d880 [size=4]
	I/O ports at d800 [size=8]
	I/O ports at d480 [size=4]
	I/O ports at d400 [size=16]
	Memory at febbc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=64
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fea00000-feafffff
	Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: nVidia Corporation A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at febb8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. A8N-VM CSM Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at febb7000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at d080 [size=8]
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

03:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GS] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: eVga.com. Corp. Unknown device c624
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at bc00 [size=128]
	[virtual] Expansion ROM at fe9e0000 [disabled] [size=128K]
	Capabilities: <access denied>

04:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. A8V Deluxe or A8N-VM CSM Mainboard
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at feaff800 (32-bit, non-prefetchable) [size=2K]
	I/O ports at cc00 [size=128]
	Capabilities: <access denied>

04:08.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01) (prog-if 10 [OHCI])
	Subsystem: NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at feafe000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

04:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs SB0410 SBLive! 24-bit
	Flags: bus master, medium devsel, latency 64, IRQ 17
	I/O ports at c880 [size=32]
	Capabilities: <access denied>

```

Here is my output of aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Other outputs are available at my Launchpad bug submission which is located [here]("https://bugs.launchpad.net/ubuntu/+bug/222778/comments/3").

Thanks for the help!

---

### Post by IgnacioMiller on 2008-04-27
Any thoughts?

---

