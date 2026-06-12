---
title: "Strange Videoproblems with i810 (Xv?)"
date: 2007-02-07
forum: Multimedia &amp; Video
---

### Post by sys on 2007-02-07
Hi

 I've discovered video problems: Videos are generally very bright, the contrast is wrong and a black (mpeg) screen isn't really black but full of greyish pixels and (mpeg)blocks.

I'm running edgy on an AcerLaptop with i810 video chip and self-compiled 2.6.20 kernel.
I unfortunately don't know when these problems started, cause at first I just thought it's because of the video material (it looks like old VHS). I just realized that it's wrong with every video.

I made a few experiments with several players (mplayer, gxine, totem(gstreamer,xine)) and discovered the following magic:

When I restart my Xserver _only_ mplayer play the vid correctly, with correct colors etc.
When I watch the video with gxine or totem it's wrong. BUT: Once I watched the video with totem or gxine just one time and close it then, mplayer starts to display it uncorrect too! I have to restart the XServer again for mplayer playing it correctly again.

There's one exception to this rule: When using totem-xine, it won't display it correctly, but it doesn't spoil my mplayer afterwards, so when I close it, mplayer still works. When using gxine or totem-gstreamer, mplayer output is always spoiled afterwards.


I just don't know what to do, any ideas?
greetings
fabian

---

### Post by brambi on 2007-02-14
Several people have this problem and AFAIK nobody found a solution.

More info here:
[https://launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/32963](https://launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/32963)

---

