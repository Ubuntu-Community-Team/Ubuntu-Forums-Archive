---
title: "padsp fails because libpulsedsp.so cannot be preloaded"
date: 2012-09-23
forum: Multimedia Software
---

### Post by jamyskis on 2012-09-23
I have a few games (Anomaly Warzone Earth, Torchlight to name a couple) that require the use of OSS for sound. I've tried passing them through padsp, which throws up this error message.

> 
jamyskis@jamyskis-UBUNTU:/usr/lib/x86_64-linux-gnu$ padsp /opt/anomaly/anomaly 
ERROR: ld.so: object 'libpulsedsp.so' from LD_PRELOAD cannot be preloaded: ignored.
AL lib: oss.c:169: Could not open /dev/dsp: No such file or directory
OpenAL sound device name: No Output


I'm running 64-bit Ubuntu 12.04 and have no problems with ALSA under PulseAudio on my Soundblaster X-Fi Titanium. It is suggested by a post [here]("http://blog.pdark.de/category/game/") that the problem is that a 32-bit application is trying to access a 64-bit library, which is why libpulsedsp.so cannot be loaded.

Is there any kind of workaround for this?

---

### Post by jamyskis on 2012-09-23
Just a quick update - I've downloaded Anomaly 64-bit from the Humble Bundle site instead of the Ubuntu Software Centre, and the 64-bit version works even without padsp.

Still remains with Torchlight though.

---

