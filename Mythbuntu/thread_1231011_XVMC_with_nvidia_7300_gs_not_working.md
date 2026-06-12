---
title: "XVMC with nvidia 7300 gs not working"
date: 2009-08-04
forum: Mythbuntu
---

### Post by neoneddy on 2009-08-04
I've tied for a while now to get Xvmc working, I'm playing a 1080p mkv right now, and my CPU is at 102%.

I've tried using a few drivers via Envy currently on 180 

I don't see a B/w OSD, I've tried removing all playback profiles except the xvmc one from CPU -- 

Am I missing something?

from the terminal :

shawn@MythTV:~$ cat /var/log/Xorg.0.log | grep Motion
(II) Loading extension XVideo-MotionCompensation

Looks like it's being loaded.  but my playback is always choppy.. 720p content play fine.

---

### Post by newlinux on 2009-08-04
1. XvMC only adds hardware acceleration for mpeg-2 content, and my guess is your mkv file isn't mpeg-2.

2. For me, I couldn't get XvMC working for 720p and 1080i content unless I created a specific profile that attempted to use XvMC on all resolutions. It only worked with one of them and crashed on the other before I did that (don't remember which one).

---

