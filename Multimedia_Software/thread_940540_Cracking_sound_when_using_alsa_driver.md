---
title: "Cracking sound when using alsa driver"
date: 2008-10-07
forum: Multimedia Software
---

### Post by Ghaagsheblah on 2008-10-07
Hi all,

Was wondering if any of you know the solution for my problem. Whenever i use the alsa driver for audio playback i have a lot of cracking in the sound. It works fine for me when using the OSS driver but in certain programs i can't find how to set them to use OSS instead of Alsa.

My version of Ubuntu is still 7.10 but plan on changing to 8.10 once it is fully released. 

My version of alsa-base is currently 1.0.14-1ubuntu2.

---

### Post by suryaoruganti on 2008-11-06
I have the same problem. Only the OSS option works for me. I just shifted from ubuntu 7.10 to ubuntu 8.10. ALSA worked fine for me in gutsy. Now, all i can hear is a crackling noise when i put any other option apart from OSS. 
OSS works fine but i want to find out what's wrong with ALSA.
Also, now i cant play sound in two applications simultaneously, both of which utilise the speakers.
I cant pause rhythmbox and see a video in VLC for instance.
Please help.

---

### Post by suryaoruganti on 2008-11-06
Hey ! i found the solution.
just right-click on the audio control beside the date on the top.
open audio control, increase the FRONT, MASTER, and PCM to the max.
That did the trick, no more cracking.
And now i can pause tracks and watch a quick video too!

---

### Post by DarrenCarlton on 2008-11-07
Thank you, suryaoruganti!

I experienced the same problem, and your solution worked!

---

### Post by CharlieFoxtrot on 2008-11-07
Thanks, suryaoruganti! My control labels were different than yours but I just moved every applicable one to max and it solved the problem of crackling sounds between tracks when playing Pandora.

---

### Post by jblanca_val on 2009-01-02
Quick reply to thank you. Same problem same solution, I was starting to be quite worried.

---

