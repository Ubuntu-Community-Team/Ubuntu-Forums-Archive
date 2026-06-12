---
title: "gstreamer is stretching videos with xv"
date: 2010-10-11
forum: Multimedia Software
---

### Post by lastexyle on 2010-10-11
After installing Ubuntu 10.10 and enabling the proprietary nvidia drivers. I've noticed a rather large problem with video playback in Totem.

As far as I can tell, it seems to think that I'm using a 4:3 monitor when I, in fact, have a 16:10 widescreen monitor. As a result everything is stretched horizontally.

To illustrate, here are some screenshots of the test video output in gstreamer-properties with automatic/xv and no xv settings:

no xv, what things should look like:
[[IMG]http://imgur.com/YAERS.png[/IMG]](http://imgur.com/YAERS.png)

Automatic/xv:
[[IMG]http://imgur.com/lLmbG.png[/IMG]](http://imgur.com/lLmbG.png)

Possibly related: When I first installed Ubuntu (pre-nvidia drivers), it detected my monitor resolution as 1400x1050 instead of 1680x1050, which I thought was odd since Ubuntu hasn't had trouble with this in years.

Any help finding the cause and/or solving this issue would be great!

EDIT: Possibly relevant: mplayer doesn't have this problem no matter what the video output is set to.

---

### Post by lastexyle on 2010-10-12
Really, no one?

---

