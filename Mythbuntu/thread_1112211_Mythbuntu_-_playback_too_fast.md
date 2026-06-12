---
title: "Mythbuntu - playback too fast"
date: 2009-03-31
forum: Mythbuntu
---

### Post by MrEgg on 2009-03-31
Hi all,

I have Mythbuntu 8.10 installed and, up until now, everything was great. Now I don't know what I've done, but any recorded or live tv programs are played back too fast : they sound like they're sped up 1,5x. I can manually slow them down, but the voices still sound high pitched, and something has definitely gone wrong. Live TV, new recordings as well as old recordings (that up until now were fine) are all affected.

I've been through many setup options, but I can't find the one that will help me resolve my problem. Can anybody help?

TIA,
Egg

---

### Post by MrEgg on 2009-03-31
Answering to myself - the problem came from the following setting :
Setup - TV Settings - Playback - Use video as time base (on page 1)

Uncheck this option and everything plays at normal speed.

Egg

---

### Post by dtgolder on 2009-06-19
Hmmm...did NOT work for me (was already unchecked, but enabled it to see if it made any difference and it did not).

---

### Post by uncle hammy on 2009-06-19
I experienced the same problem way back when however, it was only with one channel, and it became quite apparent that it was something in the channels broadcast that was the problem.  

[http://ubuntuforums.org/showthread.php?t=932926&highlight=bad+channel](http://ubuntuforums.org/showthread.php?t=932926&highlight=bad+channel)

The ultimate solution (for me) was to "Enable OpenGL veritcal sync for timing"

---

### Post by eljeffe on 2009-12-12
Ironically the fix for me was to DIS-able the OpenGL for syncing. Try both versions. I deleted a bunch of recordings before I found this. They were good, it was the front end that had the problem.

---

### Post by My Name on 2010-01-27
sorry posted in the wrong thread

---

