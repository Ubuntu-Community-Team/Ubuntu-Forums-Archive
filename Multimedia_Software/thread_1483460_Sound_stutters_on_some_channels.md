---
title: "Sound stutters on some channels"
date: 2010-05-14
forum: Multimedia Software
---

### Post by Xyldor on 2010-05-14
Hi, Im still new to ubuntu and would appreciate some help with my current problem.

Until recently my sound system worked perfectly (after much messing about).
Then I upgraded to Ubuntu 10.04 LTS (Lucid Lynx)
Since then my sound stutters on the right front and right rear speakers when playing music using Rythmbox and I am not sure what to do about it.

speaker-test -c6 -f2000 -l1    produces what sounds like static noise rather than a tone and for each channel it alternates between a pair of speakers at the same rate as the stutter observed in the right hand speakers when Rythmbox plays a music track.
I have loaded the Alsa mixer to see if I could improve things (no sucess).
 I seem to remember that previously the problems were associated with pulse-audio.

Could someone please tell me what functions alsa and pulse-audio do and how they interact? Better still, can someone suggest a solution please?

Sound card is reported by Alsa Mixer as 
Nvidia CK804 with ALC850 : Realtek ALC850 rev 0

---

