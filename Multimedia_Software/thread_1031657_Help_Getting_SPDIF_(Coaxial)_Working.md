---
title: "Help Getting S/PDIF (Coaxial) Working"
date: 2009-01-05
forum: Multimedia Software
---

### Post by BrantlyMedders on 2009-01-05
Greetings,

I'm having some issues getting S/PDIF output working.  Analog works fine, but I would like to be able to use S/PDIF for watching dvds/etc on my tv.

I have a Gigabyte GA-EP45-UD3P P45 with Realtek ALC889A audio.

According to lspci -v, my audio controller is listed as follows:
```

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: Giga-byte Technology Device a102
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at ca400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

Can anyone help me with this?

---

### Post by loboc on 2009-01-05
does 
```
aplay -L 
```
show your spdif as an available alsa device

If so then start googling about alsa configuration files and check the page for your card on alsa-project.org or somehting like that

---

