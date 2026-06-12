---
title: "Sound Problem with Ubuntu 13.04"
date: 2013-07-04
forum: Multimedia Software
---

### Post by stormcloud15 on 2013-07-04
Audio in my laptop on earphones was working fine. But suddenly recently I can hear only in left earplug. Right one is gone. I dual boot with windows 7. It works just fine there, so is not hardware problem of either Laptop or Earphones. Shall I try removing PulseAudio and Install alsa? Or any other solutions?

---

### Post by stormcloud15 on 2013-07-05
Solved it! I don't know what had happened. I opened alsamixer and there, in headphones field I increased level of both sides to full and saved this setting permanently with ```

sudo alsactl store
``` and restarted thats it.

---

