---
title: "mplayer OSD/subtitles corrupted in natty"
date: 2010-12-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Dooglus on 2010-12-07
Since upgrading to Natty a few days ago, the mplayer display is corrupted:

[IMG]http://replay.marpirc.net/chris/mplayer.png[/IMG]

Some subtitles appear just fine, others are completely garbled.  The same goes for the rest of the OSD - sometimes it's ok, mostly it isn't.

The problem goes away if I use "-vo xv", instead of my usual "-vo gl", so the bug must be something to do with OpenGL I guess.

When I run the Unity interface, a bunch of both the left and top panels are similarly corrupted.  Does Unity use OpenGL?  Could it be related?  Here's a screenshot I took when running from a live USB stick with the first alpha release on it.  I've since installed to HDD and updated, but it looks much the same:


Any suggestions as to what's going wrong here please?

Here are some shell commands that might be useful:

chris@vikki-old:~/Desktop$ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]

chris@vikki-old:~/Desktop$ glxinfo | grep "direct rendering"
direct rendering: Yes

chris@vikki-old:~/Desktop$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: X.Org R300 Project

chris@vikki-old:~/Desktop$ 

Chris.

---

