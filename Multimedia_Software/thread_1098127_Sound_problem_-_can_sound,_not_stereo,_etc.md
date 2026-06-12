---
title: "Sound problem - can sound, not stereo, etc?"
date: 2009-03-16
forum: Multimedia Software
---

### Post by takutosuki on 2009-03-16
Hi! I also have problems with my sound in Ubuntu, and it's just barely noticeable but still a bit annoying. The sound is allover bad, like the MP3 had bad sound, but i've tried every bitrate and videos, and also different programs, but it's the same problem, so I guess it's the driver.
I'm running ubuntu 8.10 (multi-booting) on a HP Pavillion dv6500 and the sound works perfectly in Windows Vista.

As I wrote, the sound sounds like the Mp3 is in a low bitrate, or inside a tin can, or like my speakers are old, and I'm guessing that it's not stereo, and it sounds like it's seriously missing some bass. Other than that, speech is almost better (when i watch movies), so it might be a problem with preferences somewhere? equalizer somewhere? i tried different programs so it's not one program's equalizer at least...

this is what i found when I did a "lspci -v":


00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
	Subsystem: Hewlett-Packard Company Device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f6480000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	Memory behind bridge: f6100000-f61fffff
	Capabilities: <access denied>

***I looked in the hardware driver program that comes with ubuntu, and i found no sound card driver. AM I MISSING A SOUND CARD DRIVER?? where can i download the correct one?***

Anyone have any ideas? thanks!

---

### Post by takutosuki on 2009-03-21
bump...
this is a really annoying problem, seriously. i don't feel like listening to music anymore! >_<

---

