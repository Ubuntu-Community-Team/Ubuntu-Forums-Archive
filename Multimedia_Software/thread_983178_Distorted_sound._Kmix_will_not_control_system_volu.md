---
title: "Distorted sound. Kmix will not control system volume."
date: 2008-11-15
forum: Multimedia Software
---

### Post by _axiom_ on 2008-11-15
*In a nutshell:*  

Sound does not work on startup.
**sudo alsa force-reload ** will make it work again, but has a lot of distortion. Can't change the system sound with kmix.



*More details:*
KDE give message that Audigy SE [SB0570] (CA0106) card does not work, and that it is falling back to default.

No sound works in any application.

In my kde system settings, each time I start up, it sets the Audigy soundcard to be my default, (which I am pretty sure is my actual sound card), but I get no sound.

If I change it to prefer the HDE ATI SB (ALC883 Analog), sound will work, but I can't control the volume.  (It sounds like it is turned all the way up, all scratchy).

Kmix has the  HDE ATI SB card settings, but they are all muted, nothing I change there  affects the volume.

I'm pretty sure that before, sound was running though the audigy card (driver?) but I didn't pay that much attention, because it was working fine.

P.S. I've seen notes that turning down the PCM volume will fix this, but I ran alsa-mixer and PCM doesn't seem to be one of the options...

---

