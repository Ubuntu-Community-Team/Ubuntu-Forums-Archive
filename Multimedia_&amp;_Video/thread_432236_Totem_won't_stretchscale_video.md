---
title: "Totem won't stretch/scale video"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by dangling participle on 2007-05-03
Hello everyone,

I have beryl installed, and as a result I was having a problems with Totem not looking correct when  I was moving the player window or  when I would switch desktops using the cube, the screen would flicker.  I got around this issue by running
gstreamer-properties

and changing the video driver for output from autodetect to xv.  Now that issue is resolved , but i have a new issue,  I cannot stretch the size of my video, when I resize the window, the video stays the same size.

I had this issue in mplayer as well, the way to resolve it was by editing /etc/mplayer/mplayer.conf and changing this section to true:

# Enable software scaling (powerful CPU needed) for video output
# drivers that do not support hardware scaling.
zoom=yes


I'm guessing its the same issue in totem, but I don't know where to change that.  Any ideas?

---

