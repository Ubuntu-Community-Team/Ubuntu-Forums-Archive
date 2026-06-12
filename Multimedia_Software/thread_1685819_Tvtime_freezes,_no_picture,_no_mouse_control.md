---
title: "Tvtime freezes, no picture, no mouse control"
date: 2011-02-11
forum: Multimedia Software
---

### Post by dianemeeks on 2011-02-11
I have been using Tvtime for several years and never had trouble with the video until now.  Now it opens, but it's frozen.  There is no picture and no sound, just a black screen that I can't control in any way.  Even to close it, I have to go through the terminal. 

I can still get channels using Mplayer, so the tuner should not be the problem. However, it is an Hauppauge 950.

I was using Lucid on both partitions. Initially, one quit, but not the other.  About a month later the other quit while I was watching which makes me think it may be something I have simply hit on the keyboard.  I have since upgraded to Maverick on one and reinstalled Tvtime to no avail.

Any suggestions would be greatly appreciated.

---

### Post by dianemeeks on 2011-02-27
I don't know if this helps, but when I try Tv-viewer, I get a segmentation fault error.  Any suggestions?

---

### Post by dianemeeks on 2011-03-03
SO the segmentation fault was a red herring, but here's something I stumbled on.  With the cable unhooked, tvtime is fine. It responds to the mouse.  It just has no signal.  However, hook up the cable and open it and I get a black, unresponsive screen.

---

### Post by dianemeeks on 2011-03-03
Unbelievably, I found the problem, and it was so simple.  I'm embarrassed to say, but the channel was causing all that trouble. I had been configuring through the terminal, apparently incorrectly, to change the channel from one that doesn't exist on our system.  When I went into the xml file and changed it, the problem was solved.

---

