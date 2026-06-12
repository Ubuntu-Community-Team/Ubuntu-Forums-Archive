---
title: "low ringing sound when starting webcam, no video"
date: 2011-03-21
forum: Multimedia Software
---

### Post by maddbaron on 2011-03-21
Video was already choppy since upgrade to 10.10, updated my xorg and now webcam is not working and I hear a ringing sound... its a lenovo webcam

system specs

AMD Athlon II Dual Core M320

Gnome 2.32.0 / Ubuntu 10.10 Maverick

Linux 2.6.35-28 Kernel

ATI Fire GL Driver

```
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200] (prog-if 00 [VGA controller])
	Subsystem: Lenovo Device 3949
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 7000 [size=256]
	Memory at f2300000 (32-bit, non-prefetchable) [size=64K]
	Memory at f2200000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200 Series
OpenGL version string: 3.3.10362 Compatibility Profile Context



```

Help please

---

### Post by no2498 on 2011-03-22
with the cam plugged in in a terminal type lsusb click enter
is the cam in the list


do you have cheese installed to try the cam with
it comes up in sound and video or in graphics

sudo apt-get install cheese

the cheese help FAQ'S try the first ? if you need too

---

### Post by maddbaron on 2011-03-24
> **no2498 said:**
> with the cam plugged in in a terminal type lsusb click enter
is the cam in the list


do you have cheese installed to try the cam with
it comes up in sound and video or in graphics

sudo apt-get install cheese

the cheese help FAQ'S try the first ? if you need too

it's a built in cam...it sits in my laptop's monitor... cheese gives me the same ringing, i tried it in skype and it didn't work, opened cheese and nuthin.. my system recognizes its a lenovo webcam but it just won't work.

---

### Post by no2498 on 2011-03-25
open a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto

---

