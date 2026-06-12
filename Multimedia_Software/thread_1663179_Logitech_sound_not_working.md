---
title: "Logitech sound not working"
date: 2011-01-09
forum: Multimedia Software
---

### Post by jojoguy10 on 2011-01-09
Hello,

I have the Logitech S-120 series speakers.  I have Ubuntu 10.10, and I can;t hear any sound.  I'm sure there has been some discussion about this, but I can't find it.  I made sure of all of these basic troubleshooting ideas:

Speakers are plugged-in
Volume control directly on the speakers is all the way up
the computer volume is all the way up
I check all the sliders in the GNOME ALSA Mixer were all the way up

But, I still don't hear anything.

I have provided some text from a "dmesg.output" and "lspci.output" files.  I hope they help!

```
lspci:

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
	Subsystem: Micro-Star International Co., Ltd. KT6 Delta-FIS2R (MS-6590)
	Flags: medium devsel, IRQ 22
	I/O ports at c400 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: VIA 82xx Audio
	Kernel modules: snd-via82xx
```
```
dmesg:
[   12.098679] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   12.098864] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
```

jojoguy10

P.S. they are not the WHOLE file.  If you want the whole thing, just ask :)

---

