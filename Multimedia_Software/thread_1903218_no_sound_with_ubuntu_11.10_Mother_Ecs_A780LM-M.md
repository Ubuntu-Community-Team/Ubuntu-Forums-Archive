---
title: "no sound with ubuntu 11.10 Mother Ecs A780LM-M"
date: 2012-01-01
forum: Multimedia Software
---

### Post by gabak on 2012-01-01
it does nt work well when i play any video at youtube
it does play some sound when pc start and other stuff like that
but when i play a video it goes to mute by itself

---

### Post by lidex on 2012-01-04
> **gabak said:**
> it does nt work well when i play any video at youtube
it does play some sound when pc start and other stuff like that
but when i play a video it goes to mute by itself

Do step one on this page:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

No joy? Post your alsa-info. Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

