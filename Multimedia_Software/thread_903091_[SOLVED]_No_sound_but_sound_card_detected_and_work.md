---
title: "[SOLVED] No sound but sound card detected and works fine"
date: 2008-08-27
forum: Multimedia Software
---

### Post by Metaleks on 2008-08-27
Hiya,

In short: I have no sound at all. From a fresh Ubuntu install. I've scoured the forums, wiki, and everything else google spat out at me, but to no avail. I've read the comprehensive guide and even tried it out, but nothing. The funny thing is, my sound card is detected, and it's working fine. Nothing is muted.

Results of aplay-l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Results of lspci -v:
```
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
	Subsystem: Dell Unknown device 0157
	Flags: bus master, fast devsel, latency 0
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe900000-feafffff
	Prefetchable memory behind bridge: e8000000-f7ffffff

00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
	Flags: fast devsel
	Memory at fecf0000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0157
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0157
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ff60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0157
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ff40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0157
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 0157
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fe800000-fe8fffff

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Unknown device 0157
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Memory at febffc00 (32-bit, non-prefetchable) [size=1K]

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Dell Unknown device 0157
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at fe00 [size=8]
	I/O ports at fe10 [size=4]
	I/O ports at fe20 [size=8]
	I/O ports at fe30 [size=4]
	I/O ports at fea0 [size=16]

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
	Subsystem: Dell Unknown device 0157
	Flags: medium devsel, IRQ 3
	I/O ports at eda0 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Dell Unknown device 0157
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at ee00 [size=256]
	I/O ports at edc0 [size=64]
	Memory at febffa00 (32-bit, non-prefetchable) [size=512]
	Memory at febff900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc R350 AH [Radeon 9800] (prog-if 00 [VGA controller])
	Subsystem: PC Partner Limited Unknown device 0470
	Flags: bus master, stepping, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at de00 [size=256]
	Memory at fe9e0000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at fea00000 [disabled] [size=128K]
	Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800] (Secondary)
	Subsystem: PC Partner Limited Unknown device 0471
	Flags: bus master, stepping, 66MHz, medium devsel, latency 64
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Memory at fe9f0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

02:02.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
	Subsystem: Creative Labs Unknown device 1003
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at cf20 [size=32]
	Capabilities: <access denied>

02:02.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
	Subsystem: Creative Labs Unknown device 1003
	Flags: bus master, medium devsel, latency 64
	I/O ports at cf18 [size=8]
	Capabilities: <access denied>

02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
	Subsystem: Dell Unknown device 0157
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at fe8ff000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at cf40 [size=64]
	Capabilities: <access denied>
```

Any ideas? Thanks in advance! :)
[B]
Edit: Issue solved. Read post #3.[/B]

---

### Post by markbuntu on 2008-08-28
Did you look in System/Preferences/Sound and see what the choices are?
Did you select the one your speakers are hooked up to?
Did you do the same thing with the little speaker icon on the top panel when you right click on it?
Did you set up the prefernces there?
Did you turn up the volumes in the mixer and unmute everything?

Have you tried my guide?

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

I apologize in advance for the longwindedness of it but when you try to be comprehensive about fixing sound problems in linux......
Anyway, there are a pile of links there that should lead to a solution for you eventually.

---

### Post by Metaleks on 2008-08-29
Just updating this thread to say that this issue is **now solved**. What I did was disable the onboard sound chip through the BIOS, and reinstalled Ubuntu. So, Ubuntu ended up installing without ever detecting the presence of the onboard sound card that was interfering with my regular sound card. I tried blacklisting the chip before reinstalling, but to no avail. Hopefully this will help someone.

---

