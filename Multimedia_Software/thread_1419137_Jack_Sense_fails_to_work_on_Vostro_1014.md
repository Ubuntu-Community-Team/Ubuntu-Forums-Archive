---
title: "Jack Sense fails to work on Vostro 1014"
date: 2010-03-01
forum: Multimedia Software
---

### Post by arky on 2010-03-01
The audio plays both on speakers and headphones, try all varients of snd-hda-intel model=[ref, auto, dell, dell-bios, etc] but doesn't fix this problem.

cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant ID 5067

Laptop: Vostro 1014
OS: Jaunty
Kernel: 2.6.28-18-generic
ALSA : 1.0.18-ubuntu11

---

### Post by Yellow Pasque on 2010-03-01
You need a more recent ALSA to fix this: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/477154](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/477154) 
This script makes it easy:
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by arky on 2010-03-02
Settled for simple workaround now. Created two shortcut keys to enable and disable headphones.

amixer sset Master frontleft mute
amixer sset Master frontleft unmute

---

