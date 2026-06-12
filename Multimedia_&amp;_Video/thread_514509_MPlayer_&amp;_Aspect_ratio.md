---
title: "MPlayer &amp; Aspect ratio"
date: 2007-07-31
forum: Multimedia &amp; Video
---

### Post by SoulScythe on 2007-07-31
To start off, I'm fairly new to linux. I've been using Ubuntu for maybe 5 months now (first Edgy and now Feisty), and its been a learning experience. Through liberal use of google, I've figured out how to install/configure/run anything and everything I could possibly need, and so far Ubuntu has been great.

However, I think I've just run into a problem I can't seem to figure out, even after searching in all the usual places online. I have mplayer installed with all the right codecs, but I've run into a minor hitch with aspect ratios. My monitor is set at 1280x1024, and while mplayer plays 16:9 video correctly, it stretches 4:3 to be full screen. With every other media player I try there are small black bars to the top and bottom, but none on mplayer. I would just view the video files with another player, but from what I understand wmv9 encoded media only works with mplayer.

It's a small issue but it seriously irks me, especially since all the help I've found from searching only talks about widescreen monitors. I'm just curious, is there a way to fix it or am I just going to have to get used to the slight distortion?

[edit] Side note: I've tried setting the aspect ratio by right clicking and selecting 4:3, this only produces a strange and empty popup with no buttons or text aside from the word "ERROR!" in the title bar.

---

### Post by shirilover on 2007-08-01
add the following to ~/.mplayer/config

monitoraspect=5:4

---

### Post by SoulScythe on 2007-08-01
Awesome, thanks so much! Everything is working like a charm now. :)

---

