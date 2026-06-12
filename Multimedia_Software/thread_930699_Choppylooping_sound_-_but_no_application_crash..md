---
title: "Choppy/looping sound - but no application crash."
date: 2008-09-26
forum: Multimedia Software
---

### Post by jimdrewes on 2008-09-26
***  I posted this in the comments of the guide sticky post, but there weren't any responses.  ***

I have a strange issue that I've been trying to resolve, and I've not yet been able to find a solution. I've gone through the guide, and it didn't help.

My sound is choppy/loopy. Ubuntu 8.04. As soon as you hit the login screen, the drum sound starts looping. You log in, and it goes away. Then, if you try playing another sound file, that file starts looping. If I do speaker-test, the white noise loops. The odd thing is, it actually progresses (gradually) through whatever the sound file is. So take the drum sound for example... it plays 1/2 of a second of sound, loops back, then progresses about 1/10th of a second into the file, and plays another 1/2 second. (At least, this is how is sounds). I had an MP3 running for hours, and when I came back it was about half-way through the song.

Another thing - it hasn't always been this way. I've not changed hardware. I've not recently upgraded Ubuntu. In fact, I can't think of anything I've done differently.

So, here are some of my outputs...

jim@jim-storage:~$ lspci -v
```

00:00.0 Host bridge: ALi Corporation M1647 Northbridge [MAGiK 1 / MobileMAGiK 1] (rev 04)
	Flags: bus master, medium devsel, latency 0
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>

00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller (prog-if 00 [Normal decode])
	Flags: bus master, slow devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: ea000000-eb5fffff
	Prefetchable memory behind bridge: eb700000-efffffff

00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
	Subsystem: ALi Corporation ASRock 939Dual-SATA2 Motherboard
	Flags: bus master, medium devsel, latency 32, IRQ 9
	Memory at e9800000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c4) (prog-if fa)
	Subsystem: ASUSTeK Computer Inc. A7A266 Motherboard IDE
	Flags: bus master, medium devsel, latency 32, IRQ 255
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at d400 [size=16]
	Capabilities: <access denied>

00:06.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
	Subsystem: ALi Corporation ASRock 939Dual-SATA2 Motherboard
	Flags: bus master, medium devsel, latency 32, IRQ 9
	Memory at e8800000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
	Subsystem: ALi Corporation ALi M1533 Aladdin IV/V ISA Bridge
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
	Flags: bus master, stepping, medium devsel, latency 32, IRQ 5
	I/O ports at b800 [size=256]
	Capabilities: <access denied>

00:0a.0 Ethernet controller: Lite-On Communications Inc LNE100TX (rev 20)
	Subsystem: Kingston Technologies Unknown device f002
	Flags: bus master, medium devsel, latency 32, IRQ 10
	I/O ports at b400 [size=256]
	Memory at e7800000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at 30000000 [disabled] [size=256K]

00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
	Flags: medium devsel

01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3] (rev a3) (prog-if 00 [VGA controller])
	Subsystem: VISIONTEK Unknown device 001b
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 11
	Memory at ea000000 (32-bit, non-prefetchable) [size=16M]
	Memory at ec000000 (32-bit, prefetchable) [size=64M]
	Memory at eb800000 (32-bit, prefetchable) [size=512K]
	[virtual] Expansion ROM at eb7f0000 [disabled] [size=64K]
	Capabilities: <access denied>

```

jim@jim-storage:~$ aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And finally...

jim@jim-storage:~$ speaker-test
```
speaker-test 1.0.15

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 2048 to 16384
Period size range from 1024 to 1024
Using max buffer size 16384
Periods = 4
was set period_size = 1024
was set buffer_size = 16384
 0 - Front Left

```

Any help would be much appreciated.

---

