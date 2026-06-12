---
title: "Video editing"
date: 2007-01-08
forum: Multimedia &amp; Video
---

### Post by LeXz on 2007-01-08
Okay, here's the thing
I have a film in jpg files (each file is a frame from that film).
I'm looking for a tool which could convert those images to an avi.

---

### Post by uuwatti on 2007-01-09
that program would be Stopmotion, unfortunately if you do apt-get stopmotion, you won't get a program that works. they say the bug is fixed in the new version, but at least for me the problem hasn't gone away with it.

---

### Post by kebes on 2007-01-09
It seems that "mencoder" can input/output a sequence of bitmap files (png, jpeg, etc.). In the [manpage ]("http://linuxreviews.org/man/mencoder/")they even give an example, like this:
mencoder "mf://*.jpg" -mf fps=25 -o output.avi -ovc lavc -lavcopts vcodec=mpeg4

mencoder (part of the mplayer package) can output just about any video type you can imagine. However it's a commandline system with hundreds of options, and can be quite intimidating at first. (Not sure how much commandline experience you have.)

Hope that helps.

---

