---
title: "Stuttery video watching live TV only"
date: 2009-05-01
forum: Mythbuntu
---

### Post by RTucker on 2009-05-01
Hi,

I have a persistent problem with my mythbuntu system which is now running 9.04. When watching digital TV, the video is not smooth, the best way I can describe it is that it looks like a game thats running at around 10 frames per second. It doesn't get better or worse, and the sound and picture quality are both fine, its just the constant jitter with the video. Also, this only affects live TV, DVDs and video files from the HDD are fine.

I would put this down to bad reception (DVB-T signal hovers around 50%) BUT if I RECORD something off tv, then go to 'watch recordings' and watch it, its perfect. Its jerky on the screen when its 'live' but the recorded copy is fine. However, if I pause/rewind tv and then play it directly from the cache in 'live tv', its still choppy.

This does not effect analog tv from the same tuner card (hybrid DVB-T/Analog).

The System:
Pentium 4 530 (3.0GHz)
1GB DDR RAM
Nvidia 6600GT 128MB (PCIe 16x)
Samsung SATA HDD (sudo hdparm -i /dev/sda1 shows udma5 mode)
Leadtek DTV2000H Version J

Any thoughts would be greatly appriciated.

---

### Post by AlecJ on 2009-05-01
I have the same Video card, and it's doing to you what it did to me.
Here's how I fixed it..
temp fix (just to prove it's the same fault)
while in live TV go Menu then Video scan then select anything and enter, that should clear the jitters.

proper fix (update drivers)
Go here and add the Ubuntu_Repository
[http://www.avenard.org/media/Home.html](http://www.avenard.org/media/Home.html)
Then update.

---

### Post by RTucker on 2009-05-01
That worked perfectly!

I can't believe it was so simple after all this time...

I reselected 'detect' under video scan and the jitter stopped immediately. I've added the repos and am running the update as we speak. Thank you, you are a god among men.

:D

---

