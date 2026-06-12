---
title: "problem videoplayback ubuntu 64"
date: 2009-02-23
forum: Multimedia Software
---

### Post by sn0m on 2009-02-23
Hi guys
I've got ubuntu 64 on my machine, which also has an ATI Radeon 3450 videocard.
I've got a problem with video playback, it flicks +++. Is there anyway to get rid of it??
Regards
Sokol

---

### Post by jbrown96 on 2009-02-23
That's a significant problem with ATI cards. There are a few things that can help. Download and install the newest drivers from ati.com. I use VLC, but there are methods if you use other players (I just don't know them). Tools===>Preferences===>Video. Find the "output" menu. You will need to try various modes, but I've found that X11 and openGL tend to work much better. Also, disabling Compiz will also help. [phoronix.com]("phoronix.com") has a lot of information about Linux graphics drivers, so you should check that out periodically. This month's drivers were just released, so check back around this time in March.

---

### Post by sn0m on 2009-02-23
Thanks jbrown, problem was sorted by installing the 64 driver from amd website. Ubuntu admin should make this available as obviously the other one dosen't work ok.
Thanks again
Sokol

---

