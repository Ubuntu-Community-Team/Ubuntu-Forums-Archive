---
title: "ATI Radeon Mobility driver"
date: 2006-12-02
forum: Multimedia &amp; Video
---

### Post by klecu on 2006-12-02
Just thought I'd be proactive and let people know how I fixed my problem with the ATI proprietary driver.

The problem was, after I installed the proprietary ATI driver ([http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")) and restarted the computer/X server, my laptop screen showed no video and had this weird effect of the screen getting brighter and slightly changing colors. Since I'm a n00b, I tried the same thing several times and even reinstalled Ubuntu. Then I learned some more about Xorg X11 and the /etc/X11/xorg.conf file and started playing around. I realized that when I ran aticonfig --initial it added a line to the device section called "Viewport". I commented that out and haven't had a problem.

So, comment out any lines that say "Viewport" as this does seem to disable all outputs. And commenting it out/erasing it does not affect the performance at all. I even got dual head with the s-video out to work.

Speaking of which, it wasn't hard at all. Just run aticonfig --initial="dual-head", open xorg.conf, comment out the "Viewport" lines as explained above, and restart X. If you don't have the s-video port connected AND the TV turned on, it will not be enabled!! If the TV shows no video either restart X (CTRL-ALT-BACKSPACE) or enter the following command in the terminal: sudo aticonfig --enable-monitor="lvds,tv". This enables the laptop screen and the TV port. If you're not using a laptop it would be --enable-monitor="crt1,tv". You must have all screens in the list or they will be turned off (max of two of course). The problem with the second option there is if you had the TV running while the xserver was on, unplugged it and plugged it back in, it gives you garbage on the screen. So, unless you haven't plugged in the screen since starting X, restart X to get the TV going.

Anyway, Ubuntu pwns.

---

