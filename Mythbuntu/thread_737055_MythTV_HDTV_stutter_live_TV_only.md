---
title: "MythTV HDTV stutter live TV only"
date: 2008-03-27
forum: Mythbuntu
---

### Post by Prefader on 2008-03-27
Got a weird one for us:

My mythbox is a 3.0 GHz P4, 512MB RAM, GeForce 7300 with a PVR-350 and a PCHDTV 5500 running mythbuntu 7.10.  Up until a couple of weeks ago, everything was fine and dandy with it - I was using the CPU++ profile (no xvmc) to watch everything.  From time to time I'd get some stuttering watching HDTV, but not often.  For the last 2 weeks, however . . .

It started with constant stuttering when watching HDTV, didn't matter if it was live or pre-recorded.  Modified the profile to use xvmc for HDTV, and it went away.  Fine and dandy, except a few days later it started stuttering again, only this time it only stutters when watching live HDTV.  SDTV works fine, and pre-recorded HDTV works fine.  So, if I start watching a digital broadcast in livetv, it stutters.  If I then hit "record", back out to the menu, and go watch the ongoing recording, it plays back fine.  What gives?

I haven't changed anything on this system, aside from running regular updates.  To be honest, I have no idea where to look for more troubleshooting.  I've tried switching deinterlacers (shouldn't matter though, all of the HDTV I'm watching is 720p), defragging my /myth partition (XFS), and using different decoder profiles (libmpeg2, ffmpeg, xvmc).  Any help is greatly appreciated.

---

### Post by laga on 2008-03-27
You're probably experiencing this problem: [http://svn.mythtv.org/trac/ticket/5025](http://svn.mythtv.org/trac/ticket/5025)

---

### Post by Prefader on 2008-03-27
Thanks!  I'll tweak my profile settings to see if I can work around that.

---

### Post by NeoMatrixJR on 2008-08-28
So how do the rest of us who don't speak bugtracker fix this?

---

