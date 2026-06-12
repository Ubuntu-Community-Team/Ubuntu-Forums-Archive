---
title: "No sound, new Ubuntu install 8.04, C-Media 6501"
date: 2008-05-06
forum: Multimedia Software
---

### Post by WanderingOtaku on 2008-05-06
I have been trying for a few days to get my sound working. It seems there are a lot of problems with this onboard audio device. I had a previous install of Ubuntu from 7.14 that I got the sound to work, but due to messing something up I had to do a clean reinstall (and then found the fix for my problem after doing so hah.) Now that I have installed 8.04 I have no sound, and can not get anything to get it to work.

I am dual booting with Windows XP, and the sound works fine there. I have found I can play videos and music in the Totem Movie Player (2.22.1) and Rythmbox Music Player, but that is the only place I get it. I have tried youtube, tried playing games in WINE, tried VLC and some others.

I have tried various solutions but only one seemed to do anything. This one allowed me to play the test beep sound in both USB audio and ALSA settings in the Sound menu. The sounds seem to play in Totem on both. It wa slate last night, and I forgot what method I used when it started working >.<

One more thing, I do have a soundcard in one of my PCI slots, but I dont intend to use it, nor does the sound work from it. I am probably going to take it out soon.

here is some information for anyone who might help... Thank you, any suggestions are appreciated.

lsusb

> [SIZE="1"]
Bus 002 Device 004: ID 0d8c:0201 C-Media Electronics, Inc. 
Bus 002 Device 003: ID 1532:000d  
Bus 002 Device 002: ID 1038:0210 Ideazon, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
[/SIZE]

lspci -v

(sorry about the formatting at the end.. I dont know what happened and I cant fix it. It really wants you to know my capabilities are denied I guess. :neutral: )
> 
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
	Subsystem: ASUSTeK Computer Inc. A8N-E Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f1)
	Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
	Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at fc00 [size=32]
	I/O ports at 4c00 [size=64]
	I/O ports at 4c40 [size=64]
	Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fe02f000 (32-bit, non-prefetchable) size=4K
	Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe02e000 (32-bit, non-prefetchable) size=256
	Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f3) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f043:815a
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at e800 size=16
	Capabilities: <access denied>

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. A8N-E Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at 09f0 size=8
	I/O ports at 0bf0 size=4
	I/O ports at 0970 size=8
	I/O ports at 0b70 size=4
	I/O ports at d400 size=16
	Memory at fe02c000 (32-bit, non-prefetchable) size=4K
	Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at c000 [size=16]
	Memory at fe02b000 (32-bit, non-prefetchable) size=4K
	Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=128
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fdf00000-fdffffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
	Subsystem: ASUSTeK Computer Inc. Unknown device 812a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe02a000 (32-bit, non-prefetchable) size=4K
	I/O ports at bc00 size=8
	Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: f8000000-fbffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
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
	Capabilities: <access denied>

01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 81fe
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at fdfff000 (32-bit, non-prefetchable) size=2K
	I/O ports at ac00 [size=128]
	Capabilities: <access denied>

01:06.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
	Subsystem: Creative Labs SB0090 Audigy Player
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at a800 size=32
	Capabilities: <access denied>

01:06.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
	Subsystem: Creative Labs SB Audigy MIDI/Game Port
	Flags: bus master, medium devsel, latency 32
	I/O ports at a400 size=8
	Capabilities: <access denied>

01:06.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (prog-if 10 [OHCI])
	Subsystem: Creative Labs SB Audigy FireWire Port
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at fdffe000 (32-bit, non-prefetchable) size=2K
	Memory at fdff8000 (32-bit, non-prefetchable) size=16K
	Capabilities: <access denied>

05:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 0740
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at fa000000 (32-bit, non-prefetchable) size=16M
	Memory at d0000000 (64-bit, prefetchable) size=256M
	Memory at f8000000 (64-bit, non-prefetchable) size=32M
	I/O ports at 9c00 [size=128]
	Expansion ROM at fbfe0000 [disabled] size=128K
	Capabilities: <access denied>

[/SIZE]

aplay -l

> [SIZE="1"]**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy [Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/SIZE]

---

### Post by aciel on 2008-07-15
Did you ever solve this? I have a C-Media 8738 instead, but seems like the same issue. (Even worked before I re-installed with Ubuntu 8!)

---

### Post by aciel on 2008-07-15
Oh, incidentally, the access denieds in your lspci are because you're not root. Do sudo lspci -v instead.

---

### Post by k.mooijman on 2008-07-15
i.m not sure if it is related with your problem but ubuntu 7.10 uses ALSA as sound driver and ubuntu 8.04 uses PULSE 
I had a problem after upgrading and my friend advised me to change some programs like mlpayer to pulse, it resolved the problem
good luck

---

### Post by fosix on 2008-07-15
> **k.mooijman said:**
> i.m not sure if it is related with your problem but ubuntu 7.10 uses ALSA as sound driver and ubuntu 8.04 uses PULSE 
I had a problem after upgrading and my friend advised me to change some programs like mlpayer to pulse, it resolved the problem
good luck

can you please give us more details about how to change mplayer from alsa to pulse? Thanks!

---

