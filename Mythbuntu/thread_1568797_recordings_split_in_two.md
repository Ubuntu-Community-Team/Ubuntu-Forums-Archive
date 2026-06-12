---
title: "recordings split in two"
date: 2010-09-05
forum: Mythbuntu
---

### Post by benlyboy on 2010-09-05
Hi my system is running great 
Apart from one little problem. Not all the time, but often when I record tv my mythbox spits the recording in two. sometimes it will even spit it in two, but one of the recording will have the whole show, and the other one will be empty.

Anyone seen this before....?


Thanks

---

### Post by RichardK3 on 2010-09-06
> **benlyboy said:**
> Hi my system is running great 
Apart from one little problem. Not all the time, but often when I record tv my mythbox spits the recording in two. sometimes it will even spit it in two, but one of the recording will have the whole show, and the other one will be empty.

Anyone seen this before....?


Thanks

Yes, I was seeing this on my Mythdora backend.  The log showed that mythbackend was spontaneously restarting in the middle of a recording, but no indication why.  

I've changed two things.  First, my Mythbuntu frontend was incorrectly configured as a frontend/slave backend.  I changed it to a frontend only.  Second, I've updated both the frontend and backend to 0.23.1 with fixes.

Since making those changes, I haven't seen the problem.  I don't know which of those eliminated the problem -- or even if it's really fixed, since it happened only intermittently.  But I've gone for a couple of weeks now without any split recordings.

Hope this helps!

---

### Post by LowSky on 2010-09-07
if you have multiple channel lineups because of multiple tuners check to see if they are both trying to record the same show. If yes edit the recording option to only use a prefered tuner, it might help.

---

### Post by benlyboy on 2010-09-07
Thanks for the input

I will work though what you guys said and see if it helps.
Its not really that bigger deal, but it would be nice to fix it.

Thanks again

---

