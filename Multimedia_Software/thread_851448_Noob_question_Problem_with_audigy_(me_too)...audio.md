---
title: "Noob question: Problem with audigy (me too)...audio not working"
date: 2008-07-06
forum: Multimedia Software
---

### Post by Cenema on 2008-07-06
Hi,
   I'm new of Ubuntu and I'm having (me too...) a problem with the audio: I have an Audigy LS, I tried to follow "Comprehensive Sound Problem Solutions Guide v0.5e".
First, I have to say that one day I had alsa audio working, but...just once, dunno if some configuration changes I've made while tryng to enable flash sound or anything else...anyway now isn't working at all
I have two sound cards, one is the motheboard integrated (which I have disactivated from bios, or at least I'm quite sure is disactivated from bios...), and the other is the Audigy LS which works fine on windows, but on ubuntu has some problems...
If I type "aplay -l" I have:
```
 scheda 0: V8237 [VIA 8237], dispositivo 0: VIA 8237 [VIA 8237]
  Sottoperiferiche: 4/4
  Sottoperiferica #0: subdevice #0
  Sottoperiferica #1: subdevice #1
  Sottoperiferica #2: subdevice #2
  Sottoperiferica #3: subdevice #3
scheda 0: V8237 [VIA 8237], dispositivo 1: VIA 8237 [VIA 8237]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: CA0106 [CA0106], dispositivo 0: ca0106 [CA0106]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: CA0106 [CA0106], dispositivo 1: ca0106 [CA0106]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: CA0106 [CA0106], dispositivo 2: ca0106 [CA0106]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: CA0106 [CA0106], dispositivo 3: ca0106 [CA0106]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0

```
Typing lspci -v I have:
```
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
	Subsystem: VIA Technologies, Inc. K8M800 Host Bridge
	Flags: bus master, 66MHz, medium devsel, latency 8
	Memory at <ignored> (32-bit, prefetchable)
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
	Memory behind bridge: f8000000-faffffff
	Prefetchable memory behind bridge: e0000000-efffffff
	Capabilities: <access denied>

00:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs SB0312 Audigy LS
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at e000 [size=32]
	Capabilities: <access denied>

00:09.1 Input device controller: Creative Labs SB Audigy LS Game Port
	Subsystem: Creative Labs SB0312 Audigy LS MIDI/Game port
	Flags: bus master, medium devsel, latency 32
	I/O ports at e100 [size=8]
	Capabilities: <access denied>

00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RT8139
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at e200 [size=256]
	Memory at fb000000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7142
	Flags: bus master, medium devsel, latency 32, IRQ 20
	I/O ports at e300 [size=8]
	I/O ports at e400 [size=4]
	I/O ports at e500 [size=8]
	I/O ports at e600 [size=4]
	I/O ports at e700 [size=16]
	I/O ports at e800 [size=256]
	Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7142
	Flags: bus master, medium devsel, latency 32, IRQ 20
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at e900 [size=16]
	Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7142
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at ea00 [size=32]
	Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7142
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at eb00 [size=32]
	Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7142
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at ec00 [size=32]
	Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7142
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at ed00 [size=32]
	Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7142
	Flags: bus master, medium devsel, latency 32, IRQ 21
	Memory at fb001000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
	Subsystem: VIA Technologies, Inc. DFI KT600-AL / Soltek SL-B9D-FGR Motherboard
	Flags: bus master, stepping, medium devsel, latency 0
	Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 0430
	Flags: medium devsel, IRQ 22
	I/O ports at ee00 [size=256]
	Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7142
	Flags: bus master, medium devsel, latency 32, IRQ 23
	I/O ports at ef00 [size=256]
	Memory at fb002000 (32-bit, non-prefetchable) [size=256]
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

01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: XFX Pine Group Inc. Unknown device 2152
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
	Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at fa000000 [disabled] [size=128K]
	Capabilities: <access denied>

```
And sudo modprobe snd-cd0106 seems to work; no error messages. But nothing, sound doesn't work. Or better...if I go in preferences -> sound, I can set-up in various ways:
I have "VIA8237" which doesn't work, and is supposed to (Via should be the motherboard's audio card); a list of "CA0106", with which I can hear the test sound by only one of the 6 speackers (and that's all, nothing else does work), and I have "ALSA" and "OSS" (they don't work), and PulseAudio which gave and error message.
I've tried to use the "Volume regolation" but, if I click on the icon, it crashes, and I haven't found yet a shell command to start it and see why it crashes while starting...
I hope someone can help me :) :) THanks a lot!

---

