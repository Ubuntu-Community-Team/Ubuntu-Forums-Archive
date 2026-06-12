---
title: "ALSA dsnoop problem"
date: 2007-09-26
forum: Multimedia &amp; Video
---

### Post by cancrusher on 2007-09-26
Ok I have searched for and read just about every thread on alsa mixing and can;t get past this problem.  I have a dsnoop pcm setup that I can record from just fine, but when i try to record with two instances of arecord at once the second one always errors out with "Unable to open slave",  I have tried the pre-configured dsnoop without a modified asound.conf or .asoundrc, checked permissions and groups, and tried defining my own dnsoop device.  I just can't get past unable to open slave on the second recording application.

Any help is greatly appreciated

---

### Post by LordInfernus on 2008-02-04
Yes I have had the same problem and I nearly freaked out trying to solve it. Tried rewritten my asoundconf in 20 different ways. Nothing...

In the end I only had to rebuild the alsalibs (libasound2) that I downloaded directly from the alsa website and it worked. Works flawlessly now. I guess something went wrong in the ubuntu build. 

:guitar:

good luck

Lord Infernus

---

