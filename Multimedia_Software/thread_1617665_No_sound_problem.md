---
title: "No sound problem"
date: 2010-11-09
forum: Multimedia Software
---

### Post by skippylou on 2010-11-09
Hi. I have an old Asus P4SGX-MX with a builtin SoundMax Digital Audio System.  I have recently installed Ubuntu 10.10.  The audio has never worked with linux (previously used several versions of Fedora).  I have unmuted everything in alsamixer.  No sound.  I have tried to work through the "Comprehensive Sound Problem Solutions Guide" sticky on this forum.  Step 2 (lspci) gives the following info:

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
	Subsystem: ASUSTeK Computer Inc. Device 80b0
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at 9400 [size=256]
	I/O ports at 9000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

Step 3, finding the alsa driver failed.  Couldn't find anything for SoundMax or Silicon Integrated Systems; also looked under Asus.  

If I can't get a driver to work can I just buy a audio card and plug it in?  Do I have to disable the builtin audio system somehow?
I would prefer to get this one working.  Thanks for any help.  Skippy

PS I can get sound if I boot windows xp.

PPS I am still a linux beginner.  If you assume that I know nothing, we will be on the same page.

---

### Post by Yellow Pasque on 2010-11-09
The driver is snd-intel8x0. You can probably disable the onboard audio in the BIOS. Even if you get it working, sound quality will probably be noticeably bad.

---

