---
title: "Sound card not detected"
date: 2011-09-04
forum: Multimedia Software
---

### Post by illiax on 2011-09-04
Hi, i ve got this silly nasty problem i cant seem to solve. I am new to ubuntu, and recently i have installed 11.04 for the first time. Everything was good, untill i deciced to 'upgrade' my sound driver.  It did worked after the installation (only one output), but since my onboard soundcard has to outputs, i wanted to get both to work (i've done this easly on Windows :S).
After a lot of websearching, guides and everything... (also follwed alsa installation) I screwed it, and now ubuntu dont recognize my soundcard, I mean, i go to system -> preferences -> sound -> hardware and now there is nothing listed in!! (there was one device after ubuntu installation and before i screwed it u.u).
Now i really dont know what to do...
is there a way to reset the configuration? now i dont really mind having one output :S

for more information .. lspci -v shows :

Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
[INDENT]Subsystem: Biostar Microtech Int'l Corp Device 820d
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at bfffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel[/INDENT]

---

