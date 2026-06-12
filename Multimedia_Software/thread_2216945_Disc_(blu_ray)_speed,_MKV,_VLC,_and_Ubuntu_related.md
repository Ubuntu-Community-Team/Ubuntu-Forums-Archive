---
title: "Disc (blu ray) speed, MKV, VLC, and Ubuntu related."
date: 2014-04-14
forum: Multimedia Software
---

### Post by irishbum92 on 2014-04-14
Hi, so I'm streaming my blu ray discs (using this particular portable drive, the LG CP40 [http://www.lg.com/us/data-storage/lg-CP40NG10](http://www.lg.com/us/data-storage/lg-CP40NG10) ) through MKV and into VLC in Ubuntu 13.10. My only issue with this set up so far is the cache/buffer fills up, then dies back down. I have to wait for the video to unfreeze and get the disc to spin again, and this continues happen during the course of the video I'm watching.

I'm being told I can change the disc speed in the terminal with the "eject" command, but I can't seem to get it to work with this portable drive. Does anyone have any aids or relatable experience that they were able to overcome?

Thanks in advance, if there's an old thread about this somewhere, I apologize and please send me the link. I couldn't find anything (yet).

---

### Post by irishbum92 on 2014-04-14
As an elaboration, I've also done "setcd" in the terminal, but it only does it for the disc drive in the laptop, and not the portable blu ray drive. Does anyone know a way to direct it towards the blu ray drive in the terminal?

---

### Post by andrew.46 on 2014-04-15
I cannot test this at the moment but this thread:

[http://www.makemkv.com/forum2/viewtopic.php?f=6&t=3855](http://www.makemkv.com/forum2/viewtopic.php?f=6&t=3855)

has some suggestions for hdparm. Perhaps this will be at least a start?

---

### Post by irishbum92 on 2014-04-15
I've tried the hdparm command, setting the speed at "1," and it didn't do anything.

However, I think I've found a solution by some experimenting. If I set the buff size to "64 MB" in MKV, the buff rate times out but the blu ray player has enough time to still spin and encourage MKV to buffer again. 

Thanks for posting and showing the thread. It encouraged me to keep brainstorming.

---

### Post by andrew.46 on 2014-04-16
Good to see that you have found a work-around :).

---

