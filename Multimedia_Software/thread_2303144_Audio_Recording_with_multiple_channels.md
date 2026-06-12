---
title: "Audio Recording with multiple channels"
date: 2015-11-16
forum: Multimedia Software
---

### Post by mike4ubuntu on 2015-11-16
does anybody have multi-channel Audio Recording in recent Ubuntu versions (14.04 +)?  It appears that the ALSA kernel modules are broken for (v3/v4) Linux kernels for recording.  I've tried a number of PCI based cards (ice1712 m-audio Delta) and USB (Focusrite Scarlette) interfaces and nothing seems to work for record reliably.  Playback seems ok for the most part.  However, for recording either only a single stereo channel is available or there is way too much distortion.  I've tested the devices on Windows where they work fine for recording, but not on Linux.  I've tried adding a .asoundrc file and tried jackd, but nothing seems to help.  I know that these interfaces worked previously in the 2.6 kernel versions, but apparently not now with the more recent versions.

Does anybody have a multi-channel audio interface working for record in the latest Ubuntu versions?

---

