---
title: "Low sound output"
date: 2010-01-28
forum: Multimedia Software
---

### Post by MooPi on 2010-01-28
I'm converting an older model laptop with an ATI chipset to Ubuntu. I believe I have the correct driver in use for sound but am getting very low sound output. No sound through the laptop speakers, and minimal(whisper) from headphones. To have usable sound I've connected the amplified speakers to the sound jack. Even with everything cranked to the max sound is just usable. I'm attaching the results of alsa-info.sh in text form in hopes someone with audio knowledge will be able to discern my problem. I've gone through the sound troubleshoot threads without gleaning any info. TEXT INFO:

---

### Post by ajgreeny on 2010-01-28
In a terminal run ```
alsamixer
``` if you have not already done so, and check if any of the sliders that shows are muted or too low. Use cursor keys to move from slider to slider and raise up and down for their levels, "M" to mut/unmute and tab to move from Playback to Capture to All.  Eswc to exit.  It often finds things you won't even know are there, and are perhaps, set far too low.

---

### Post by MooPi on 2010-01-28
Thanks but I have done this and many other things before posting. I've read several post on sound and modules and nothing so far.

---

