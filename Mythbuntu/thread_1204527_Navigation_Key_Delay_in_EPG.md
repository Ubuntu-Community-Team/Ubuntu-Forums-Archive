---
title: "Navigation Key Delay in EPG"
date: 2009-07-04
forum: Mythbuntu
---

### Post by orygunjon on 2009-07-04
I am experiencing a 2-30 second delay between hitting a keyboard navigation key and having the cursor move in the Program Guide (EPG). Not experiencing any delays outside of MythTV or within MythTV in other components (Setup, etc.)

The problem is intermittent.  Sometimes(rarely) navigation works fine, sometimes it delays.  Delays also occur on other keys - i.e. [ESC] when attempting to exit program guide.

Built 7/3/2009 from Mythbuntu 9.04

Live TV is fine. Guide use is OK after waiting for delay.

Hardware:

AMD Athlon LE1620
1 GB RAM
160 GB HD
1 TB HD
NVIDIA GeForce 6100 onboard graphics.
HDHomeRun Tuner

---

### Post by crez79 on 2009-07-04
This is a known problem but I don't know what the proper fix is. I think this is caused by the little screen playing live tv. Try it by first pausing tv and then going into guide. When I did this, everything was fine. If I didn't pause it, I got delays. I just disabled playback while in guide in one of the setup screens. Easiest solution for me and the lack of the little screen playing tv was no problem for me.

---

### Post by uncle hammy on 2009-07-05
This issue is one of the oldest there is with MythTv.  There have been numerous reported fixes, and honestly none has done it.  As indicated, the safest bet is to pause before entering the guide.  With my setup up, I have actually narrowed the issue down to specific channels. I.E. I have zero issues on channels that are broadcast in 1080i, and EPG delays on channels that are broadcast in 720p.  It's also 100% consistent, as in ALL my 1080i channels are fine, and ALL my 720p channels have troubles.

---

