---
title: "Audacity issue with 7.04"
date: 2007-09-03
forum: Multimedia Production
---

### Post by myrightangle on 2007-09-03
Over the weekend I updated my system from 6.10 to 7.4. Everything works fine (or better) except Audacity.

I use Audacity for recording from my USB turntable. Under 6.10 I could record and play a track at the same time. 

With 7.4 I can record and I can playback, but not at the same time. Audacity reports:"Error while opening sound device" when ever I have Software Playthrough enabled.

I've tried all the solutions at the Audacity Wiki site. Is there some weird sound sharing issue with 7.10? Is there a way to install the older version of Audacity (1.2.4 from 1.2.6) to see if that version has the same problems?

Thanks In Advance.

---

### Post by zettberlin on 2007-09-04
Try the following:

1.: install aoss - the advanced alsa-oss compatibility layer
2.: start audacity with:

aoss audacity

this makes audacity run for me same time with amarok an the like....

---

### Post by myrightangle on 2007-09-08
I downgraded to Audacity 1.2.4b from the Ubuntu 6.10 archives. Playback is now working. I can only surmise that a change in 1.2.6 caused the problem.

Thanks,

---

### Post by pelicanghost on 2007-09-08
how do you go into earlier repos?

And synaptic wont let me force version on audacity

---

