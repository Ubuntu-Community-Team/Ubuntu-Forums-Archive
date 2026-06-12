---
title: "Changing the default alsa output"
date: 2008-09-04
forum: Multimedia Software
---

### Post by dash2 on 2008-09-04
I have an IBM X60 running Hardy. My sound doesn't work too well. For example "aplay send.wav" sounds crackly and distorted. However, "aplay -Dplughw:1 send.wav" sounds nice. This sends the sound direct to the (AD1981) sound card. Is there a way I can set up ALSA to always use plughw:1 instead of hw:0 as default? Can I also make e.g. the flash plugin use this?

---

### Post by Lawrence Talbot on 2008-09-15
Look under preferences - sound and you should be able to change that setting there.

---

