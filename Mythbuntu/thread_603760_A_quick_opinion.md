---
title: "A quick opinion"
date: 2007-11-05
forum: Mythbuntu
---

### Post by Just4Fun20 on 2007-11-05
First... for fun, to explore and to learn I've installed MythTV over a dozen times in the last 6 months on various flavors of Linux.  MythBuntu is by far the slickest and least problematic install I've completed so far.  My previous favorite was MythDora.  

My TV is capable of 1080i although I don't have any cable signal to drive that.  My MythBuntu box is connected via Component (YPbPr) at 1920x1080 through a GEForce 6600 Card.  It won't matter to my question but my capture card is a PVR-150.  

I 'recycled' a machine.  It's a 3.0Ghz P4 chip with 512MB of memory.  I believe the HD is IDE.  FSB is 400/533/800 and I don't know which speed it's running.  Unfortunately (I've read some bad reports) my MoBo uses the VIA chipsets (North Bridge VIA P4M800, South Bridge VIA VT8237R)

I downloaded a 'test' file that is encoded in High Definition (1080P) format.  This is an .mkv file, which I'm not familiar with, but which plays fine (well almost).  

The problem is that after about 30 seconds the  video and audio playback develop a sort of stuttering problem.  Every second or so it  sort of skips for a split second and then continues.  

I'm assuming the system just can't keep up, but before I gave up on HD (with my current equipment) I just wanted to get a quick sanity check.  

Would you assume this should work or is my assumption about the Hardware not being up to the task a good one?

---

### Post by tgm4883 on 2007-11-05
What video card are you using?

---

### Post by Just4Fun20 on 2007-11-05
Specifically it's a BFG GeForce 6600 GT OC / 128MB GDDR3 / AGP 8x / Dual DVI / HDTV / Video Card.  

Overall, it's been a pretty good card.  Dramatic overscan at 1080i but the fix for that is fairly well documented.

---

### Post by tgm4883 on 2007-11-05
Hmm, maybe it's the via chipset causing problems.  You should have enough power to do 1080p, I would think.  Have you tried enabling xvmc?

---

### Post by superm1 on 2007-11-05
> **Just4Fun20 said:**
> First... for fun, to explore and to learn I've installed MythTV over a dozen times in the last 6 months on various flavors of Linux.  MythBuntu is by far the slickest and least problematic install I've completed so far.  My previous favorite was MythDora.  

My TV is capable of 1080i although I don't have any cable signal to drive that.  My MythBuntu box is connected via Component (YPbPr) at 1920x1080 through a GEForce 6600 Card.  It won't matter to my question but my capture card is a PVR-150.  

I 'recycled' a machine.  It's a 3.0Ghz P4 chip with 512MB of memory.  I believe the HD is IDE.  FSB is 400/533/800 and I don't know which speed it's running.  Unfortunately (I've read some bad reports) my MoBo uses the VIA chipsets (North Bridge VIA P4M800, South Bridge VIA VT8237R)

I downloaded a 'test' file that is encoded in High Definition (1080P) format.  This is an .mkv file, which I'm not familiar with, but which plays fine (well almost).  

The problem is that after about 30 seconds the  video and audio playback develop a sort of stuttering problem.  Every second or so it  sort of skips for a split second and then continues.  

I'm assuming the system just can't keep up, but before I gave up on HD (with my current equipment) I just wanted to get a quick sanity check.  

Would you assume this should work or is my assumption about the Hardware not being up to the task a good one?

Mplayer 1.0~rc2 can play matroska container files (typically h264/ac3 in those) much better.  I just packaged it up for Hardy yesterday.  After it gets built on the buildd's, I'll get a backport setup for it to come to gutsy for those interested.

I seriously can't wait until all the other FFMPEG projects (mythtv, xine, vlc, gstreamer) all get this new ffmpeg merge with this support done.  It is great :)

---

### Post by Just4Fun20 on 2007-11-06
Thank you very much for the sanity check.  I will research XVMC, which I'm not using (and don't know what it is :-) ).  Also, it appears that perhaps it's the player or codec.  Bottom line is that it should probably work and I should invest some time trying to resolve the problem.  

Thanks again.

---

