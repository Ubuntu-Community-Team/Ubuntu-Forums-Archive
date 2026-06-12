---
title: "Audio Stuttering on 11.04"
date: 2011-10-05
forum: Multimedia Software
---

### Post by Lazaruss on 2011-10-05
I have Ubuntu 11.04 installed on a Lenovo B560. Whenever I'm playing music, usually with Spotify for Linux, the sound starts to stutter, degenerating into sequences of tones, as if small sections of the music are played as short tones. I can stop it by closing and reopening spotify, but I can't work out what's causing it. I have no idea where to look in logs.

My Sound Card: 
```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Lenovo Device 38af
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at f2800000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

---

### Post by lcman on 2011-10-05
Did you try installing latest drivers from intel's website?

---

### Post by Lazaruss on 2011-10-05
As far as I can see, the drivers aren't available on the intel website, plus they're a kernel module anyway, loaded by alsa. I've tried specifying the mode to load snd-hda-intel in alsa-base.conf, have to wait and see if it works

---

### Post by EllieDragonfly on 2011-10-16
I have the same problem, sound stutters. My computer: Ao751h.

---

