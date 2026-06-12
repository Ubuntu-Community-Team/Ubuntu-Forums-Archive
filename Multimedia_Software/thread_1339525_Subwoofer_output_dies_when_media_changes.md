---
title: "Subwoofer output dies when media changes"
date: 2009-11-27
forum: Multimedia Software
---

### Post by perfectsync on 2009-11-27
Hi, i've just did (a week ago) an new fresh install of ubuntu karmic, everything is nice :) except one thing, that actually drives me crazy, when watching movies / lissen to music, about everytime (almost) it changes media i have to go to "system/preference/sound and change to 2 system channel and then back to 5.1 system again caus it turns of my subwoofer (and sometimes my center too it seems to anyway) is this something with pulseaudio or something in ubuntu? (onboard HDA Intel sound, even tried on my Creative Extreme Gamer X-Fi, it's the same thing there) and also (when speaking of sound :) ) when i run wine programs i have to start the same application 2 times (so it runs the two applications at the same time) otherwise there will be no sound output at all.. kinda strange? (never had either of those problem in 9.04)

---

### Post by corecode on 2010-01-04
Did you ever get this to work?  I'm having the same problem.

---

### Post by corecode on 2010-01-06
#pulseaudio helped to at least work around this issue:

I put

```
enable-lfe-remixing = yes
```into daemon.conf and now I have a workgin subwoofer signal.

---

### Post by Gone fishing on 2010-01-10
> enable-lfe-remixing = yes

worked for me too

---

### Post by donarntz on 2011-01-11
Changing LFE may have worked for me, I haven't had time to really check.  Another problem I have noticed since hooking up a sub and changing to 4.1 is that when Ubuntu sound effects play, the sound is completely garbled.  Is this a known bug or workaround?

Thanks,

Don

---

