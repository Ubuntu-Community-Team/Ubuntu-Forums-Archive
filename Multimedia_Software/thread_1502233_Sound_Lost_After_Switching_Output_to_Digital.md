---
title: "Sound Lost After Switching Output to Digital"
date: 2010-06-05
forum: Multimedia Software
---

### Post by RiazM on 2010-06-05
My sound was working, but I got a new SPDIF cable, so I switched it to digital. It worked fine. But then I restarted and now it's gone.

aplay -l tells me I have no soundcard but lspci -v lists


00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: ASUSTeK Computer Inc. Device 836c
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f9ff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

So my soundcard is there. Any advice on how to progress?

---

### Post by RiazM on 2010-06-05
Just fixed it by doing

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils ubuntu-desktop  

```

---

