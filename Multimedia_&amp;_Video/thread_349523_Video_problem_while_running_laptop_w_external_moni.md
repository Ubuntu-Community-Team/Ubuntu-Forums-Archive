---
title: "Video problem while running laptop w/ external monitor"
date: 2007-01-30
forum: Multimedia &amp; Video
---

### Post by drstrangenorm on 2007-01-30
I am having a problem with my Toshiba laptop while using an external monitor.  Everything works fine and I configured the xorg.conf file to properly handle the resolution of the new monitor.  But there is one problem.

When I play any type of video at all, in any type of program, I get a blue screen where the video should be playing.  During this I can only hear sound.  It is almost as if its running in a weird dual monitor mode and wont overlay into the ext CRT.  

However when I play the videos on the LCD they run fine!

Any one else ever have this problem?  I've done some searching and can't find a solution.

---

### Post by shiinto on 2007-09-22
I'm haveing the exact same problem. Any help with this would be much appreciated...

---

### Post by shiinto on 2007-09-22
I just tried this on my comp and worked like a charm. Got perfect picture now.

Go to terminal type in: gstreamer-properties

This should bring up a dialogue box with some options. Click the Video tab.

Then, for the output change it to: X Window System (No Xv)

That's it... 

I hope this works for ya... peace....

---

