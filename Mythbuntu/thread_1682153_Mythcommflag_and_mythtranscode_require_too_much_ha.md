---
title: "Mythcommflag and mythtranscode require too much hand-cranking"
date: 2011-02-05
forum: Mythbuntu
---

### Post by kheston on 2011-02-05
I've set up Mythbuntu 10.04 with an HVR-2250 (works fine) and am having trouble getting shows to transcode and have their commercials flagged consistently.  I have to kill one or more mythtranscode or mythcommflag processes every day or so.  When things stops working, strace-ing the problem process yields a "No more queue slots" or "Failed to decode frame.  Position was: 0" message. 

The standard answer to rectify the problem involves checking the process list when you notice a problem and killing hung processes.  I'd like to be a little less hands-on with this and was wondering whether there's a solution out there already that monitors these processes.

Is there any way to fix this other than killing the process and wiping  the job queue?

---

### Post by kheston on 2011-02-06
More research...

My guess is mythtranscode and mythcommflag are hanging up errors in the recordings themselves.  When I view the problematic ones in mplayer, there are lots of digital artifacts that it chokes on in the files.  Any way to get mythtranscode and mythcommflag to exit when they see things like this?

---

### Post by GuiGuy on 2011-02-19
> **kheston said:**
> More research...

My guess is mythtranscode and mythcommflag are hanging up errors in the recordings themselves. 

I'm not so sure. I'm having the same problem and it's only surfaced since upgrading to 10.10 and 0.24.

... gotta go now and kill another run away mythcommflag job...

Cheers

---

### Post by kheston on 2011-02-19
GuiGuy,  How does your video look when you play it in something like VLC or mPlayer?  No problems in the capture?

---

### Post by GuiGuy on 2011-02-20
> **kheston said:**
> GuiGuy,  How does your video look when you play it in something like VLC or mPlayer?  No problems in the capture?

I'm getting slight tearing on transcoded files. Again, only since 10.10 and 0.24. 

Live TV and recorded files are fine.

---

### Post by kheston on 2011-02-24
Looks like I'm not out of the woods either, just had to kill mythcommflag.  It had been working on a 1 hour show for a day and a half.

---

### Post by cshive on 2011-03-13
I've had these issues with 10.04 and .23 as well.  Mostly seen on the show Fringe.  I haven't found a fix for it, though I've tried this with limited success:
```
mythtranscode --mpeg2 --buildindex --allkeys --showprogress --infile "$1"

```
I've also manually edited the cutlist for several episodes then successfully transcoded.  Only reasonable explanation I've found is there is some problem with the video stream.  Shows that fail look fine to me, but that's all I've got.  I was hoping an upgrade to the newest release of mythtv would solve some of these issues.  Waiting until I have a full weekend to work on it any further though.

---

