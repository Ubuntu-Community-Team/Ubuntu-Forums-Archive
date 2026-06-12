---
title: "[SOLVED] playing a game system through composite on pvr500"
date: 2008-04-21
forum: Mythbuntu
---

### Post by taehC on 2008-04-21
I am trying to get to play my game systems on my comp.  I have a pvr500 with 2 composite inputs.  Is there anyway to play the system on my comp?  Can I use mplayer?  I have tried with the wii and have gotten like 5 sec control delays on mythbuntu.  Can anyone show me a guide or help me out?

---

### Post by superm1 on 2008-04-21
Unfortunately the pvr-500 always passes stuff through the mpeg2 encoder.  This is what is introducing your delay.  No way that i've heard to grab the raw stream before that.

---

### Post by taehC on 2008-04-21
Ok! thx for helping me out!

---

### Post by laga on 2008-04-21
Try /dev/video16 (or was it 24?) to get the raw stream. I'm not sure how well this will work, though. There'll still be some delay.

---

