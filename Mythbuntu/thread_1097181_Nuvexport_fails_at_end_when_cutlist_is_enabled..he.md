---
title: "Nuvexport fails at end when cutlist is enabled..help?"
date: 2009-03-15
forum: Mythbuntu
---

### Post by freddyg on 2009-03-15
Hey guys, doing some research here, but not finding much.
I cant successfully run nuvexport when I enable use cutlist. It fails out with "mythtranscode died early" at the very end, about 99.6%.  This leaves me with a usable file, but it makes it difficult to do a batch of files as it crashes and stops the process entirely. 
I'm running 8.10 and saw the same issue in 8.04 but never have found a solution. 
running dual pchdtv 5500s dvb-t cards on a dual core athlon, gigabyte board. 
I've tried running all the svn versions of the involved packages, but that hasnt helped either. am i missing a step somewhere, or is there a setting that involves this?
I cant help but think that its me thats the issue as i'm not seeing this anywhere...at least with any solutions.
thoughts?
thanks

---

### Post by klc5555 on 2009-03-15
> **freddyg said:**
> Hey guys, doing some research here, but not finding much.
I cant successfully run nuvexport when I enable use cutlist. It fails out with "mythtranscode died early" at the very end, about 99.6%.  This leaves me with a usable file, but it makes it difficult to do a batch of files as it crashes and stops the process entirely. 
I'm running 8.10 and saw the same issue in 8.04 but never have found a solution. 
running dual pchdtv 5500s dvb-t cards on a dual core athlon, gigabyte board. 
I've tried running all the svn versions of the involved packages, but that hasnt helped either. am i missing a step somewhere, or is there a setting that involves this?
I cant help but think that its me thats the issue as i'm not seeing this anywhere...at least with any solutions.
thoughts?
thanks

This won't help you if you're trying to encode to mp4, but if you're coding to avi or mpg or one of the other formats that this handles, it may help to try using "./nuvexport --transcode" rather than the default that runs with ffmpeg. It will avoid all the glitchy incomprehensible ffmpeg errors that can drive you crazy and the final  product will be of higher quality. I started using the --transcode switch because in my case (doing avi's) ffmpeg would always die when starting its second pass. This, of course, was after the first pass had taken some twelve to fifteen hours to complete.

---

### Post by freddyg on 2009-03-15
Hey Klc, thanks, i'll give it a try, see what happens, i dont think i've even seen that switch before.
12 to 15 hours? what the heck were you converting? wow!
BTW, just a bit more information, what i'm attempting is a xvid conversion using mencoder...sheesh i'm out of it today.

UPDATE:
the --transcode switch helped matters, allows the job to complete without errors.  
now to do battle with getting nuvexport to run as a user job....more research!!!
thanks
fred

---

