---
title: "Crappy sound quality."
date: 2009-06-13
forum: Multimedia Software
---

### Post by GAZ082 on 2009-06-13
Hi guys. I have an integrated sound card with the HDA VIA VT82XX chipset (this is what the sound config dialog says).

The sound quality was great until i decided to switch everything from Autodetec to Pulse Audio. Then the sound started to be trashy, like a radio with no good signal. Went back to Auto, nothing. Tried ALSA, OSS, still the same crap.

Just for the sake of more information, sounds stops when the ALSA mixer's PCM is muted.

Any ideas? Tried some tips from the Audio FAQ and other threads, no luck :(

Edit: I'm using 9.04!

---

### Post by expelledboy on 2009-06-14
Change the setting back to what they were when everthing was working, then turn up PCM to 90%.

---

### Post by kostkon on 2009-06-14
Yeah, it must be the PCM volume level that causes this problem. Try to lower it a little, like *expelledboy* suggested, maybe to 90% or 80%.

Also, it would be better to change put your playbacks in your sound preferences back to Autodetect.

---

### Post by GAZ082 on 2009-06-15
I reinstalled Ubuntu and still crappy sound. It annoys me that i have to decrease the PCM, just to increase the master volume and find the noise. I believe some update ****** up something.

---

