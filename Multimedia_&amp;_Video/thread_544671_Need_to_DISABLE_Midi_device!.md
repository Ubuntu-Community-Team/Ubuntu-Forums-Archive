---
title: "Need to DISABLE Midi device!"
date: 2007-09-06
forum: Multimedia &amp; Video
---

### Post by Jaaxx on 2007-09-06
Yep, believe it or not, I need to KILL a midi device!

I have a generic (Dynex) soundcard which uses the ICE1724 chipset.  The midi port which is created causes the system to lockup when it is accessed.  All other midi devices work properly, but apps like Rosegarden try to connect to the ICE port and crash the system.  I simply need to prevent the offending port from being assigned in the first place without disabling the sound card (cannot blacklist ICE1724)

midi port shows up as 16:ICEnsemble ICE1724

I might add that the ALSA module doesn't provide an option for this.
This is not a routing issue either, simply LOOKING at /dev/midi causes a crash, while /dev/midi1,/dev/midi2 etc, no problem...

---

