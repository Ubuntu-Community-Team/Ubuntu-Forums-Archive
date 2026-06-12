---
title: "Choppy DVD playback in mandriva 2008.1"
date: 2008-07-09
forum: Mandriva/Mageia
---

### Post by SunnyRabbiera on 2008-07-09
Alright, I decided to give mandriva 2008.1 a try on my computer... I got all the codecs and stuff installed but DVD playback is crap.
I tried every mode, turned my desktop effects on and off but its still choppy...
anyone got ideas?
and yes, I tried the video playback plugin in compiz, its a no go.

---

### Post by AdamWill on 2008-07-09
Check DMA modes are right on your DVD drive. From the console, do:

hdparm /dev/hdc

(or whatever device is your DVD drive) and post the output here.

---

