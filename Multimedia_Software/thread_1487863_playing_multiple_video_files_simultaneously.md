---
title: "playing multiple video files simultaneously?"
date: 2010-05-19
forum: Multimedia Software
---

### Post by byronvn on 2010-05-19
Hey, this may be an odd question.  I need to play two video files simultaneously and be able to pause and play them simultaneously as well.  It would be even more helpful if I could skip forward and backward (5 sec, 15 sec, whatever) in both files simultaneously, but I can live without this if necessary.  The files are all 2GB, about 30min, 720x480 MPGs shot with a Sony Handycam.  I have no audio requirements at all.

I'm very new to Ubuntu.  I used to be somewhat proficient in Linux years (decades?) ago, never having used XWindows much.  I see Lucid comes with Totem Movie Player 2.30.1, though it doesn't look like it's going to be much help in this.

Anyone know of any way I can do this, or am I out of luck?  I've been looking around online for a solution but can't seem to find any.  (In MS Windows, I had created a mouse script with shortcuts on the task bar.  Clicking the appropriate shortcut would then select one video window, press pause, select the second video window, press pause, etc.  Very clumsy.)  

Any help would be greatly appreciated!  

Thanks!
byronvn

---

### Post by xzero1 on 2010-05-19
Simply run two instances of mplayer. I have tested this on my sysetm by playing a dvd and an x264 file. I use the default radeon driver and default video output. Your biggest issue will be if your video driver supports this and of course your overall computer configuration. 

:confused:On first viewing, I must have missed the part about simultaneously pausing and stuff. You could do the same thing as in windows but I would think you might be able to capture keyboard input via a batch trap mechanism and selectively control the players. If that fails you should be able to suspend and resume the mplayer processes (kill -STOP p1# p2# and kill -CONT p1# p2#).

---

