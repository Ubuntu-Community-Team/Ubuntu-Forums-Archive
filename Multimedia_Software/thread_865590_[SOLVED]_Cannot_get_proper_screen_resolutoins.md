---
title: "[SOLVED] Cannot get proper screen resolutoins"
date: 2008-07-20
forum: Multimedia Software
---

### Post by the_ on 2008-07-20
I'm running xubuntu...

I can not get a proper screen resolution. I have 2 options - 640x480 and 320x240 both of which are way too small.

I used Envy to install the proper nVidia drivers and restarted, everything worked well, I selected the resolution I wanted, 1024x768, and everything was fine. Then I restarted X...

Things are back the way they are. I tried uninstalling and reinstalling the nVidia driver but that didn't work. 

Here's lspci -v:

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3) (prog-if 00 [VGA controller])
	Subsystem: nVidia Corporation Unknown device 015a
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 19
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at f4000000 (32-bit, prefetchable) [size=64M]
	Memory at f3f80000 (32-bit, prefetchable) [size=512K]
	[virtual] Expansion ROM at f0000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [44] AGP version 2.0


sudo dpkg-reconfigure xserver-xorg doesn't work, just gives me choices about keyboard layout, nothing about screen resolution.

I tried adding the resolutions to /etc/X11/xorg.conf also without success.

I should also add I tried installing it manually without Envy before with no luck.

---

### Post by NT4usB on 2008-07-21
(install and) run:```
sudo nvidia-settings
```

Did you try dpkg with the -phigh switch?
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by the_ on 2008-07-21
> **NT4usB said:**
> (install and) run:```
sudo nvidia-settings
```
I have it installed and I looked at it before. I don't see where that application will help me... I don't see anything to do with screen resolution, maybe it's just me though.

Did you try dpkg with the -phigh switch?
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Doesn't work.

Maybe I should note when it was detecting the resolutions properly, I got a nVidia splash screen for a quick second on startup. I don't anymore.

---

### Post by xc3RnbFO8P on 2008-07-22
Try
atl+f2
gksudo displayconfig-gtk
Choose Generic
and resolution that your monitor supports.

---

### Post by the_ on 2008-07-22
> **Ringi said:**
> Try
atl+f2
gksudo displayconfig-gtk
Choose Generic
and resolution that your monitor supports.

WORKED! 

Thank you! :)

---

