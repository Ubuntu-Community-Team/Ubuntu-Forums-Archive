---
title: "xserver-xorg-video-intel driver conflicts with Rhythmbox visualizer?"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by rrwo on 2007-05-05
I installed the xserver-xorg-video-intel driver rather than the xserver-xorg-video-i810 driver, since it seems to fix a few problems ith Feisty.

However, when I use the visualizer in Rhythmbox, Rhythmbox crashes and exits.

Has anybody else found this to happen?

---

### Post by dburnett77 on 2007-05-06
I had this problem also with the same driver.  I read after searching the forums it is a bug.

If you set the driver in the applications themselves, you might be able to solve the problem.

Go to the "Preferences..." section in your program.
For me, in mplayer, I had to select X11 drivers for video, then select "enable software mixer" in the audio section.

Couldn't even get gxine to start.  Hopefully it'll be fixed soon.

I figured this out from the post:
[http://ubuntuforums.org/showthread.php?t=413492&highlight=video+intel](http://ubuntuforums.org/showthread.php?t=413492&highlight=video+intel)

---

### Post by rrwo on 2007-05-23
Where in these applications do I specify a video driver?

---

