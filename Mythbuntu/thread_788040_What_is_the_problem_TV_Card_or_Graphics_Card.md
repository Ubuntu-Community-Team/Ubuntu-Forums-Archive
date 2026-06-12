---
title: "What is the problem TV Card or Graphics Card"
date: 2008-05-09
forum: Mythbuntu
---

### Post by himpantsou on 2008-05-09
I have setup a mythbuntu machine with 
- CPU = AMD x64 Dual Core 4800+ 
- Grpahics = NVidia 8500 
- TV Card = Twinhann DVB-T

My problem is that the Live TV in Myth constantly stutters (starts and stops) and in general it is not smooth. It is not poor signal quality because in that case you would see the picture granularity play up. 
I am sure it is either the Graphics or the TV Card which is under-performing but i can't thick of a test to make. Do you have any suggestion on how to figure out which card is to blame?
Cheers

---

### Post by klc5555 on 2008-05-09
> **himpantsou said:**
> I have setup a mythbuntu machine with 
- CPU = AMD x64 Dual Core 4800+ 
- Grpahics = NVidia 8500 
- TV Card = Twinhann DVB-T

My problem is that the Live TV in Myth constantly stutters (starts and stops) and in general it is not smooth. It is not poor signal quality because in that case you would see the picture granularity play up. 
I am sure it is either the Graphics or the TV Card which is under-performing but i can't thick of a test to make. Do you have any suggestion on how to figure out which card is to blame?
Cheers

How are the recordings? If they play back perfectly, then the trouble might not be either card. It might be a single-disk setup  with a slow IDE disk that's having trouble doing all the swapping/buffering/recording read/writes on one disk fast enough to keep up. I had a fair amount of stuttering (on 7.10 Myth .20.2 with a single slower IDE drive) until I moved my /recordings directory (under /var/lib/mythtv) onto a second SATA drive. Seemed to take care of stuttering, except for a couple of minutes the two times a day when mythfilldatabase runs and a script backs up mythconverg onto the second drive. 

Good luck.

---

### Post by himpantsou on 2008-05-09
I have only one SataII HDD partitioned. That should be enough surely.
The recordings do seem better but still do have some stuttering.

---

### Post by klc5555 on 2008-05-09
Well, then, just to brainstorm simple tests to try to eliminate possible causes, with the proprietary NVidea drivers installed it would seem that if you can play a DVD (or imported video) full-screen cleanly with one of Mythbuntu's included non-Myth players, then the video card is unlikely to be at fault. (You may also be able to try to play tv output from your tuner card  through one of these other players without Mythtv involved --I've never used your particular card).

If, however, the same DVD (or video)played in Mythtv's player then stutters, buffering to the HD may be the problem.

If both of these DVD/video tests come out cleanly, then heck, maybe the problem really _is_ the tuner card. 

Anyway, these would be the sort of tests I'd try at the start, just to see what might happen.

Cheers.

---

