---
title: "Can't skip ahead or back in some recordings"
date: 2013-11-20
forum: Mythbuntu
---

### Post by tomj528 on 2013-11-20
I've been running my 10.04 setup for the past 3+ years with very few problems until a couple of days ago.  Suddenly when I try to watch SOME recordings I can't skip ahead or back.  On some recordings they kick me back to the recordings menu on others there is a long delay before it skips forward, others will behave normally.  This is even an issue with older recordings too, not just the more recent ones so I'm thinking that it's something with the player perhaps?  The only other thing that I can of is that the storage hard drive is going bad.  I first noticed this on my frontend machine and then on the main frontend/backend machine too.  Any help would be really appreciated...I'm at a dead end.

---

### Post by tomj528 on 2013-11-20
I just tried to go into edit on one of the recordings and it said "No seektable".

---

### Post by aelfric55 on 2013-11-20
The seektable for that recording is corrupt. Fixing it should only take a few minutes.

Here is the wiki page for fixing it: [http://www.mythtv.org/wiki/Reparing_the_Seektable](http://www.mythtv.org/wiki/Reparing_the_Seektable)

I have usually preferred the mythtranscode option for this purpose --in my own experience mythcommflag has had difficulties fixing dvb recordings since at least Mythtv 0.20, though it has always worked great for analog recordings.  But in recent versions, mythtranscode is not necessarily a ray of sunshine either, so your mileage may vary.

---

### Post by tomj528 on 2013-11-20
Thanks aelfric55, that's exactly what it was...I finally figured it out last night about 2am...funny how sometimes you get on the trail of a solution and can't let it go.  I used mythcommflag --rebuild --all and this morning by 11am it was finished and completely fixed...I even rebooted and tried recording a new show and it's creating the seektable data for new recordings too.  I really appreciate your help because I was STUMPED!  So thanks for posting the fix!

---

