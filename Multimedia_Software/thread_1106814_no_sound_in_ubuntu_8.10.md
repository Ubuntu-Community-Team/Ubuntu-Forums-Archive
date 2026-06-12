---
title: "no sound in ubuntu 8.10"
date: 2009-03-26
forum: Multimedia Software
---

### Post by Barbelo on 2009-03-26
Hi, 
I just installed Ubuntu 8.10 and there is no sound. The soundcard was working before the installation so i dont know why. I ran lspci -v in the terminal  and i got this:

01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)
	Subsystem: LeadTek Research Inc. Device 289e
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
	Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Memory at e8000000 (32-bit, prefetchable) [size=512K]
	[virtual] Expansion ROM at e8080000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: rivafb, nvidiafb, nvidia

02:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
	Subsystem: Creative Labs Device 8064
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at a000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1

02:09.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
	Subsystem: Creative Labs Device 0020
	Flags: bus master, medium devsel, latency 32
	I/O ports at a400 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: Emu10k1_gameport
	Kernel modules: emu10k1-gp

02:0b.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at f2000000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: bttv
	Kernel modules: bttv

02:0b.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
	Flags: bus master, medium devsel, latency 32, IRQ 9
	Memory at f2001000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied>


Please help!
thanks!

---

### Post by redenex on 2009-03-26
These might help?

[http://ubuntuforums.org/showthread.php?t=1103532](http://ubuntuforums.org/showthread.php?t=1103532)
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by Barbelo on 2009-03-26
thank you sooooooo very much!!!!!!!!

---

