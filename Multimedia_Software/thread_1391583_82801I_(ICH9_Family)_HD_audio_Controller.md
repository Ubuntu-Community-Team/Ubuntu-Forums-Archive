---
title: "82801I (ICH9 Family) HD audio Controller"
date: 2010-01-27
forum: Multimedia Software
---

### Post by isomorph on 2010-01-27
i freshly installed ubuntu karmic koala 64bit on my new Dell Vostro 1520.
Headphone and Speakers work but the microphone does not work. Mixer is not on mute;)

The output of lspci -v is:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Dell Device 02bc
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f3300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


Oh and by the way I am a noob so if there is a solution please make it step by step. Thanks so much

---

### Post by isomorph on 2010-01-27
Shameless selfbumb

---

### Post by Yellow Pasque on 2010-01-27
Please don't "bumb" more than once a day (regardless of shame). [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188972](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188972)

Looking around the web, I see a lot of Vostro owners complaining about the mic and no one reporting success. If you're feeling lucky, you could try the latest ALSA: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

