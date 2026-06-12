---
title: "configure and make errors installing ALSA drivers"
date: 2007-08-04
forum: Multimedia &amp; Video
---

### Post by zerosanity on 2007-08-04
Okay, I know the root of my problem probably doesn't belong in this forum.  However, the symptom does, so here I am.  I have a VIA 8237, which calls for the VIA82xx ALSA driver, which I need to get me some MIDI playback from rosegarden and such.  So, I've downloaded the driver and ran configure (which took me a while, because configure couldn't find my kernel, so I had to find it so that I could tell configure where it was).  However, when I get to the make portion, i get the following error for several includes:
> /usr/src/linux/include/linux/irq.h:172: error: requested alignment is not a constant

resulting in this:
> make[1]: *** [hpetimer.o] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9rc4a/acore'
make: *** [compile] Error 1


Although, to most people, MIDI playback isn't a terribly big deal, i'm a composer.  This is one of the primary reasons I got Ubuntu Studio.  It's also worth noting that i've tried really hard (read: this is a several-day-old problem) to find a fix for this through google and this forum, but couldn't.  

Any help would be much appreciated.  If you want/need, I can post the entirety of the make dialog, but i'm pretty sure I got the important bits.

Thanks, Zero

---

### Post by zerosanity on 2007-08-04
Beuller?

---

### Post by zerosanity on 2007-08-04
Also, I forgot to mention that I tried the things mentioned in the sticky if that helps.

---

### Post by zerosanity on 2007-08-05
nobody?

---

