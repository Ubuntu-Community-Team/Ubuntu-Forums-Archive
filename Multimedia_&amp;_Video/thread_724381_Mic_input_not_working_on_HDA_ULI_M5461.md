---
title: "Mic input not working on HDA ULI M5461"
date: 2008-03-14
forum: Multimedia &amp; Video
---

### Post by cronholio on 2008-03-14
My mic input is not working on my onboard sound card (ASUS mainboard) with Gutsy (was the same on Feisty). Chip is an HDA ULI M5461. Mic capture appears in the mixer, I've switched it on (as well as all the other microphone related things in the mixer). In alsamixer mic capture is shown but without a slider, only CAPTUR, L and R which cannot be turned off. Does that mean mic capture is actually not present?

I've already compiled and installed ALSA 1.0.16 which didn't change anything. I also tried
```
options snd-hda-intel model=asus
```
in /etc/modprobe.d/alsa-base. Same with asus-laptop and uniwill-m31. No success.

Google doesn't seem to help. Any ideas?

Btw, sound recorder doesn't even run, telling me:

> Your audio capture settings are invalid. Please correct them in the Multimedia settings.

---

### Post by cronholio on 2008-03-14
It works now with model=3stack.

---

