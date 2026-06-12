---
title: "As if you haven't seen enough (No Sound Issues - 8.04)"
date: 2008-04-25
forum: Multimedia Software
---

### Post by d41m40u on 2008-04-25
I just installed Ubuntu 8.04 on my computer, and of course, there is no sound.  I can't say for sure if it works in any other version because I haven't had any other version on her yet.  But as it stands, I've followed the sticky on the comprehensive sound problems in every way possible, but that did not work.  (I'm not even sure if it's up-to-date, is it?)  I've also tried several other things lying about the internet.  Yes, everything's unmuted that needs to be and yes, I'm using the correct drivers.  It's an onboard sound card supposedly supported by ALSA.

Output of aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I'm using snd-via82xx which I believe is the correct driver.  Please correct me if I'm wrong.

Output of lspci -v:
```
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
	Subsystem: VIA Technologies, Inc. K8M800 Host Bridge
	Flags: bus master, 66MHz, medium devsel, latency 8
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>

00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: d0000000-efffffff
	Prefetchable memory behind bridge: 80000000-800fffff
	Capabilities: <access denied>

00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
	Subsystem: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at e000 [size=8]
	I/O ports at e100 [size=4]
	I/O ports at e200 [size=8]
	I/O ports at e300 [size=4]
	I/O ports at e400 [size=16]
	I/O ports at e500 [size=256]
	Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: VIA Technologies, Inc. VT82C586/B/VT82C686/A/B/VT8233/A/C/VT8235 PIPC Bus Master IDE
	Flags: bus master, medium devsel, latency 32, IRQ 16
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at e600 [size=16]
	Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at e700 [size=32]
	Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at e800 [size=32]
	Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at e900 [size=32]
	Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at ea00 [size=32]
	Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
	Subsystem: VIA Technologies, Inc. USB 2.0
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at f8000000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
	Subsystem: VIA Technologies, Inc. DFI KT600-AL / Soltek SL-B9D-FGR Motherboard
	Flags: bus master, stepping, medium devsel, latency 0
	Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
	Subsystem: Jetway Information Co., Ltd. Unknown device 4170
	Flags: medium devsel, IRQ 19
	I/O ports at eb00 [size=256]
	Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
	Subsystem: VIA Technologies, Inc. VT6102 [Rhine II] Embeded Ethernet Controller on VT8235
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at ec00 [size=256]
	Memory at f8001000 (32-bit, non-prefetchable) [size=256]
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

01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series] (prog-if 00 [VGA controller])
	Subsystem: VISIONTEK Unknown device 1930
	Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 20
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at e0030000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at d000 [size=256]
	[virtual] Expansion ROM at 80000000 [disabled] [size=128K]
	Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series] (Secondary)
	Subsystem: VISIONTEK Unknown device 1931
	Flags: 66MHz, medium devsel
	Memory at e0020000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>

```

---

### Post by sneakers563 on 2008-05-26
Are you using the optical out by chance?  I have the same card and I can get the analog out to work but not the optical.  It worked fine until my upgrade to hardy.

---

### Post by harlock74 on 2009-08-10
I have same chip via8237, and have analog sound working, but no optical. I'm on hardy also..can anyone help with this issue?

---

