---
title: "No Sound on 10.10"
date: 2010-11-06
forum: Multimedia Software
---

### Post by Marvin_Zindler on 2010-11-06
Hi, so I've been using Ubuntu 10.04 and installed 10.10 for AMD 64 bit to get a new vid card to work which did work, unfortunately now my sound is gone.  I've been using the on board sound on my ASUS M4A89GTD mobo. This is what's detected "card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]"  I tried the stuff at the beginning of the sticky in this forum, tried the debugger that is preinstalled with ubuntu, searched and tried a lot of stuff on google with no luck.
I really don't know much about how to trouble shoot linux and clueless when it comes to working in the terminal, but I'm guessing I could get the sound packages for 10.04 if only I had slightest clue how it's done?

---

### Post by Marvin_Zindler on 2010-11-07
Does anyone have any help? I'm not above buying a cheap soundcard that has support on this version of ubuntu.

---

### Post by Yellow Pasque on 2010-11-08
I see a lot of "upgraded to 10.10 and lost sound" threads. One solution I've seen is removing corrupt pulse files (so they get regenerated):
```
cd ~/
rm -rf .pulse*
```
Another one I've seen for laptops is pulling the AC and battery for a brief time to reset the audio chip.

---

