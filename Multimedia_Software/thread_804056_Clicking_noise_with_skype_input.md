---
title: "Clicking noise with skype input"
date: 2008-05-22
forum: Multimedia Software
---

### Post by SuperZero on 2008-05-22
Hi, I'm really new to Ubuntu and I've been trying to figure this out on my own, but at this point I'm not sure how to fix this. Skype is the only thing keeping me from complete windows avoidance.

Problem: When using skype, I produce a bizarre clicking noise every few seconds. Also, when trying to test audio recording off of System > Preferences > Sound, it seems to fizzle out.

Equipment: Quickcam Notebook Deluxe (ID 046d:09c1 Logitech, Inc.), Hardy Heron 8.04, Dell Inspiron E1505 Notebook, HDA Intel something or other

I'm pretty unfamiliar with all of the terminal commands and such. Any ideas on how to fix this? Any other information needed? Thanks

---

### Post by yochaigal on 2008-05-22
There seems to be some problems with pulseaudio in skype, you might want to try changing your settings to use ALSA instead.

System > Preferences > Sound

Change each to ALSA.


Then restart skype and see if the problem persists.

---

### Post by SuperZero on 2008-05-23
Thanks for the advice, but the clicking still persists even in alsa.

---

