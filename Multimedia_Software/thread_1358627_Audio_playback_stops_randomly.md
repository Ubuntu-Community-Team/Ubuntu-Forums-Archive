---
title: "Audio playback stops randomly"
date: 2009-12-18
forum: Multimedia Software
---

### Post by EggplantOfFire on 2009-12-18
Ok so, did a fresh install of Karmic for the second time with the same audio problems. I'll have Audacious playing something and I'll be watching a Youtube clip and suddenly all audio will just stop. I look at Audacious and the clock will read "00:00." I hit stop and then play and it starts playing again. On the Youtube clip, I hit pause and then play and the video fast-forwards for some strange reason and there is no audio. I have to restart Firefox to get it to play again. 
Audacious does this even by itself when I have no other programs running. 
I checked the forums here first and found the "Comprehensive Sound Problem Solution Guide" but that didn't seem to help. Also, when I got Ubuntu Studio up and running I did the Comprehensive Multimedia & Video How to.  

I'm running a Dell Inspiron 1420.

aplay - l returns:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: USX2Y [TASCAM US-X2Y], device 0: US-X2Y Audio [US-X2Y Audio #0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


I'm running most audio through the onboard Intel device. I use the Tascam US-122 usb audio interface for audio production, which works, though playing back mp3s or streaming audio through the Tascam is glitchy. 

lspci -v returns:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 01f3
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

I did the sound modprobe bit but to no avail. 

Help me Ubuntu forums, you're my only hope.

---

### Post by EggplantOfFire on 2009-12-18
Well I found [[COLOR="Blue"]this page[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1318058") and instructions in the second post there seems to work.

---

