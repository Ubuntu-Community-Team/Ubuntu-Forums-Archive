---
title: "Help with VLC and TOtem playing .avi..!!! PLEASE HELP!!"
date: 2009-01-05
forum: Multimedia Software
---

### Post by R3troSpy on 2009-01-05
So I just recently got into Ubuntu. Now I have a problem. Every time I try to play an .avi or .mpg file, both Totem and VLC plays them, but the players flash on and off every second, making them unwatchable. Any help please?

System Specs:
80gb HD
ATI Radeon Mobility X1400 (With restricted drivers turned on)
1gig o Ram
Intel Pentium Dual Core @ 2.1 or 3


THANKS FOR ANY AND ALL HELP!!!

---

### Post by eagleton on 2009-01-05
Please open a terminal, type "vlc" or "totem", press the return key, open a movie and tell us what the output of the terminal is while the error appears.

---

### Post by R3troSpy on 2009-01-05
Actually, I think I may have found the problem! (and fixed it)
I went into Applications > Accessories > Terminal and typed in "gstreamer-properties" and hit enter. On the video tab, I clicked the "X Window System/(No xv)" . That seemed to do the trcik for me!

Thanks to Izek!
[http://ubuntuforums.org/showthread.php?t=1010219&highlight=.avi](http://ubuntuforums.org/showthread.php?t=1010219&highlight=.avi)

---

