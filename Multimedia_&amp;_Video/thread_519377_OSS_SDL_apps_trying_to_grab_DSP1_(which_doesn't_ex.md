---
title: "OSS SDL apps trying to grab DSP1 (which doesn't exist...) and other weirdness"
date: 2007-08-07
forum: Multimedia &amp; Video
---

### Post by enigma_0Z on 2007-08-07
Wondering how to fix this, what is causing it, and what happened.


Anyway, when I run an SDL-based game (namely Sauerbraten), when SDL tries to init sound, it tries to access /dev/dsp1 (which doesn't exist) instead of /dev/dsp. I tried creating a symlink to /dev/dsp1, but then it tired to access /dev/dsp2!

What's going on here, and is there a fix out there? I can't think of anything I've changed, but if anyone has an idea, post it and I'll check. Thanks.

---

