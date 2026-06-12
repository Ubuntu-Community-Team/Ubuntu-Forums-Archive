---
title: "weird behavior from jack after kernel 2.6.32-25 update"
date: 2010-11-20
forum: Multimedia Software
---

### Post by dewdrop_world on 2010-11-20
No time at the moment to quantify (can do later), but after months of reasonably stable audio work under kernel 26.32-24, I finally updated to 25 and jack apps are crashing left and right.

Anyone else seen it? What broke?

Thanks.
James

---

### Post by dewdrop_world on 2010-11-21
I don't know exactly what it was, but I can confirm that my system is MUCH more stable with kernel 26.32-24. 25 is a problem. I guess I should file a bug.

For the record, this is what I was seeing:

- If something went wrong in the audio chain (such as SuperCollider outputting NaN, which then got stuck in a reverb unit), I would have to restart Jack. After that, audio would be choppy -- it sounds kind of like a sample rate mismatch between software and hardware but the configuration looks okay (both SC and Jack are at 44.1kHz).

- Xruns when the CPU was not even close to loaded (like, CPU use for audio processing < 10% and no other applications open).

- Conflicts between pulse applications -- such as, I shut down a VirtualBox VM while rhythmbox was playing, and playback broke. Restarting the pulse server didn't help -- other pulse apps were okay, but still nothing from rhythmbox. Reconfigured the default sink, tried gstreamer-properties -- only a reboot helped.

For now, I'd have to say, if you're doing audio work, be very very careful about that kernel upgrade!

James

---

