---
title: "HP Compaq nc6000 no sound, quick fix?"
date: 2010-08-26
forum: Multimedia Software
---

### Post by cino on 2010-08-26
Hi,

Here is what I did. Installed fresh Ubuntu and all worked fine.

Sound was working fine as far as I know. Ubuntu start up sound worked.

Decided to install LMMS for a bit of fun but there was no sound.

Removed LMMS and now am wondering how to get back to my "default" settings.

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 0890
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 3000 [size=256]
	I/O ports at 3880 [size=64]
	Memory at a0100000 (32-bit, non-prefetchable) [size=512]
	Memory at a0180000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

Eek. Can anyone help?

---

### Post by cino on 2010-08-26
Well, not a pretty way to fix it, but that's what you get when you don't program I guess;

Ran the Ubuntu live cd figuring it would re-recognise the driver, sound worked, restarted, all back and running.

---

