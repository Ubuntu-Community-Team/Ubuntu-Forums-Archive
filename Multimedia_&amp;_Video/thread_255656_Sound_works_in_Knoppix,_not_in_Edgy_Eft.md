---
title: "Sound works in Knoppix, not in Edgy Eft?"
date: 2006-09-11
forum: Multimedia &amp; Video
---

### Post by aschmitz on 2006-09-11
Hi everyone,

I'm having problems with sound on a new Gateway MX6429. I think I got the network card working, but I had been having some problems with that. That's not my current issue though, I'm having some problems with the sound card.

When I put in a Knoppix CD (I tried 4.0.2 and 5.0.1), I can hear the sounds just fine ("Startup Sequence Initiated", etc.). I believe that the startup sequence messages say that the atiixp driver is being used. If I do a lsmod, the snd_atiixp module is loaded and being used.

If I reboot into a new Edgy Eft install (fully updated), I can hear some sound, but it stutters, repeating a second several times and moving on to the next one, and repeating the cycle.

Is there any difference you might know of between the Knoppix ALSA and the Ubuntu one? Might there be some way I can see the options being used for the Knoppix autodetected module or something similar?

I'd really appreciate some help with this issue.

Thanks,
ASchmitz

---

### Post by majesticturkey on 2006-09-11
You might want to ask in the Edgy Eft forum. It's an unstable release, won't be out until October, so it's a work in progress.

---

### Post by aschmitz on 2006-09-11
Oh yeah, I forgot about that. Thanks!

---

