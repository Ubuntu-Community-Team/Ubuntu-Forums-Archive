---
title: "DVD::Rip Errors"
date: 2007-10-02
forum: Multimedia &amp; Video
---

### Post by HIM_Tattoos on 2007-10-02
Hey guys quick DVD Ripping question for you. Everytime that I go to rip a dvd with DVD::Rip it tells me:

ChapterX is to small and useless you should remove it
ChapterX is to small....... etc

So I will just click okay for all of them then I get this:

Job 'Process title #7' failed with error message:
Job 'Process preview frame - title #7, chapter #1' failed with error message:
Job 'Grab preview - title #7' failed with error message:
msg:Can't find frame 0 in VOB navigation file '/home/him/dvdrip-data/unnamed/tmp/unnamed-007-C001-nav.log' (which has only 0 frames).  at /usr/share/perl5/Video/DVDRip/JobPlanner.pm line 512

--------------------------------------------------------------------------------

--------------------------------------------------------------------------------

--------------------------------------------------------------------------------



Any ideas???

---

### Post by HIM_Tattoos on 2007-10-03
Anyone?

---

### Post by skotadi on 2007-10-03
I had the same problem.  It can't read copy-protected dvds.  You need to install libdvdcss2 to allow it to read the dvd.  I won't tell you how I installed it -- I think I did something wrong, because it broke all my multimedia (video/audio playback).  I haven't heard of that being an  issue for anyone else, however.  

It's not in the default repositories.  maybe start by going to [this]("https://help.ubuntu.com/community/Medibuntu") page

good luck!

---

