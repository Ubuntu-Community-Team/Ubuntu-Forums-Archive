---
title: "No sound on Medion all-in-one P4010"
date: 2012-12-29
forum: Multimedia Software
---

### Post by mahjsa on 2012-12-29
After a clean install of 12.10 I am again experiencing problems with the sound. Even after trying the module.options that worked in 10.10 I still have only sound on the headphones.
I have been able to trace the problem to pulseaudio by trying pavucontrol. When I mute and unmute sound (PULSE sound-indicator) I hear the sound briefly only when I unmute. After that it stays silent (except when I use headphones).
Soundcard detected as Nvidia mcp79 and/or Alc889
Module: snd-hda-intel
Tried options=targa, medion, medion-md2, 3stack-dig, 6stack-dig, auto, alc889a to no avail.

---

### Post by xc3RnbFO8P on 2012-12-29
Try 
**options snd-hda-intel model=generic**

---

