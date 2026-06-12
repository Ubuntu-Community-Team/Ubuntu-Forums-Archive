---
title: "Audio problems with games."
date: 2008-08-29
forum: Multimedia Software
---

### Post by yarjar on 2008-08-29
I am using 8.04 with PulseAudio, and it works very well except for games. Playback of music with Audacious and video with Totem works absolutely fine, and the audio has no problems. But whenever I try to play a game with dosbox or play Urban Terror the audio sometimes skips, makes random beeps, or crackles. Any way to fix this?

---

### Post by yarjar on 2008-08-29
._.

---

### Post by Crafty Kisses on 2008-08-29
Post the results of > lspci -v

---

### Post by yarjar on 2008-08-29
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
	Capabilities: [e0] #00 [fee0]

00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8239
	Flags: 66MHz, fast devsel, IRQ 5
	I/O ports at fc00 [size=64]
	I/O ports at 1c00 [size=64]
	I/O ports at 1c40 [size=64]
	Capabilities: [44] Power Management version 2

00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8239
	Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port
	Capabilities: [80] Power Management version 2

00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f043:8239
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]
	Capabilities: [44] Power Management version 2

00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at dc00 [size=16]
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
	Capabilities: [cc] HyperTransport: MSI Mapping

00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at c800 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
	Capabilities: [cc] HyperTransport: MSI Mapping

00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	I/O ports at c400 [size=8]
	I/O ports at c000 [size=4]
	I/O ports at bc00 [size=8]
	I/O ports at b800 [size=4]
	I/O ports at b400 [size=16]
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
	Capabilities: [cc] HyperTransport: MSI Mapping

00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Memory behind bridge: fde00000-fdefffff
	Capabilities: [b8] Subsystem: nVidia Corporation Unknown device cb84
	Capabilities: [8c] HyperTransport: MSI Mapping

00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 81f6
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fe020000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping

00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 504
	Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at b000 [size=8]
	Memory at fe029000 (32-bit, non-prefetchable) [size=256]
	Memory at fe028000 (32-bit, non-prefetchable) [size=16]
	Capabilities: [44] Power Management version 2
	Capabilities: [70] MSI-X: Enable- Mask- TabSize=8
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/3 Enable+
	Capabilities: [6c] HyperTransport: MSI Mapping

00:09.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8239
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 505
	Memory at fe027000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ac00 [size=8]
	Memory at fe026000 (32-bit, non-prefetchable) [size=256]
	Memory at fe025000 (32-bit, non-prefetchable) [size=16]
	Capabilities: [44] Power Management version 2
	Capabilities: [70] MSI-X: Enable- Mask- TabSize=8
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/3 Enable+
	Capabilities: [6c] HyperTransport: MSI Mapping

00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00008000-00009fff
	Memory behind bridge: fdd00000-fddfffff
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: fa000000-fcffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: [f0] #0f [0010]

01:07.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
	Subsystem: D-Link System Inc D-Link AirPlus G DWL-G510 Wireless PCI Adapter(rev.B)
	Flags: bus master, medium devsel, latency 168, IRQ 17
	Memory at fdee0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [44] Power Management version 2

01:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at fdeff000 (32-bit, non-prefetchable) [size=2K]
	Memory at fdef8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2

06:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: ASUSTeK Computer Inc. Unknown device 81e4
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fddfe000 (32-bit, non-prefetchable) [size=8K]
	Expansion ROM at fdde0000 [disabled] [size=64K]
	Capabilities: [68] Power Management version 2
	Capabilities: [50] Express Legacy Endpoint IRQ 1

06:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Unknown device 81e4
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at 9c00 [size=8]
	I/O ports at 9800 [size=4]
	I/O ports at 9400 [size=8]
	I/O ports at 9000 [size=4]
	I/O ports at 8c00 [size=16]
	Capabilities: [68] Power Management version 2

07:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GS] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: eVga.com. Corp. Unknown device c624
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at 7c00 [size=128]
	[virtual] Expansion ROM at fcfe0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint IRQ 0

---

### Post by yarjar on 2008-08-30
Was that helpful at all?

---

### Post by yarjar on 2008-08-31
No one?

---

### Post by yarjar on 2008-08-31
bump

---

