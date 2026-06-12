---
title: "No Sound on Intel 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02"
date: 2009-02-23
forum: Multimedia Software
---

### Post by mcland on 2009-02-23
I just installed ubuntu 8.10 on my machine at work.  Everything worked great, all the hardware works correctly, except my sound card.  I've tried multiple solutions posted on the forums and other websites but nothing works.  So far, it seems like my sound card is detected, but I'm guessing the drivers aren't there or something.  Here's the info about my card from lspci-v:

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
	Subsystem: IBM Device 1f00
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 6000 [size=256]
	I/O ports at 6400 [size=64]
	Memory at feaffc00 (32-bit, non-prefetchable) [size=512]
	Memory at feaff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0


If anyone has any clue how to fix this, I would be greatly appreciative!

---

### Post by Metaljaz on 2009-02-24
Do you have the volume control button on the top right corner of the screen?

If you haven't already tried this:

Right click on the volume control button, select preferences
and make sure that the Alsa mixer is selected. Select the PCM
as the device and track to control. Then double-click on the 
volume control button and make sure the device there is also 
the alsa mixer. Make sure the Master, Master Mono and PCM is 
not muted.

Then select System<Preferences<Sound from the top menu and 
test the device.

---

### Post by mcland on 2009-02-24
I've tried that already.  It didn't work, but thanks for the tip.

---

### Post by mcland on 2009-03-02
Now, for some odd reason, it's telling me that I have no sound card installed.  But the strange thing, is that I get system sounds.  As far as I know, I haven't changed anything sound related.

---

### Post by mcland on 2009-03-03
So I dug around a little more and found that I don't have alsa drivers for my kernel (2.6.27-11-generic).  However, I get errors when I try to compile them.  Does anyone know how I can go back to the previous kernel (2.6.27-7-generic) or of a way to get alsa drivers for my current kernel?

---

