---
title: "ATI Graphics -  When TexturedVideo Off - No Graphical Login"
date: 2008-11-12
forum: Multimedia Software
---

### Post by sshapiro63 on 2008-11-12
Hello All,

I am running Ubuntu 8.04 and cannot get an ATI HD 4850 to work properly when compiz is enabled. I have configured the TexturedVideo OFF option in the xorg.conf file to eliminate flicker when playing video, however, this results in no graphical login. If I set the option TexturedVideo ON instead of OFF, graphical login works fine.

Any ideas what the problem with TexturedVideo OFF could be?

Thanks,

Steve

---

### Post by 73ckn797 on 2008-11-13
If you just purchased the video card, take it back, ATI cards are not supported very well from ATI for Linux. I have given up trying to get the HD3450 card working on another machine with full effects. There are multiple remedies posted in the forums but I have yet to find one that works and after too many hours of tinkering have given up the pursuit. This is not an Ubuntu issue.

At least you have a response to you question. I have posted several and received absolutly no feedback. Other responses were one of the multiple posts I refer to.

Sounds like I have a problem, Huh?

---

### Post by roy1980 on 2008-11-13
I use the 4870 HD card, and have the same problem.

I haven't found a fix, but I have found a workaround.

Download VLC, go to tools-preferences choose the Video configuration, and force X11 video output.

Alternatively, run mplayer -vo x11 [path to file]

Then you will have no flickering in windowed or full-screen mode.

Unfortunately, it's not fast, and uses quite a bit of resources. But I can live with it, temporarily.

Cheers

---

### Post by libra1780 on 2008-12-28
after a lot of diggin i foud out that's a driver problem.
the proprietary driver is yet not so compatible with xv hardware accel. openGL actualy is quite fast, but i tried all tricks, no way to get rid of flickering in window mode, fs is perfect. I also have the problem that when im running with xv while using my dvb card, the x-server crashes..
BUT.. good news.. theyre doing giant steps.. updated to the newest driver ver today, and x-reset or restart doesn't result in a machine-crash anymore.. yuppee..
will try to switch to openGL again.. maybe no flickering anymore :)

PS. only for info.. kaffeine 0.8.6 and also 0.8.5 i think doesn't support openGL drivers due a bug. you have to compile 0.8.7 and at least xine 1.1.9. long work, but it's worth, had performance gain btw xv and opengl.. less cpu usage

---

