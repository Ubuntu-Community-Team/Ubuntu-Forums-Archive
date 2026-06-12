---
title: "mplayer pause ?"
date: 2009-11-08
forum: Multimedia Software
---

### Post by rd1381 on 2009-11-08
i installed ubuntu in clean state ( no upgrade)
and then installed smplayer and mplayer from default repository
but when i play a video it sometimes behaves like pausing (though clicking pause again doesn't resume the video) and i have to jump to another point in video in order for it to resume
i tried mplayer and smplayer from ppa (rvm ppa) but they too have this bug
anyone else has it?

my system is p5q/nvidia 9800gt (driver 185)/ubuntu 9.10 x64

---

### Post by rvm4000 on 2009-11-08
In smplayer change the audio driver from alsa to pulse.

---

### Post by rd1381 on 2009-11-09
thank you
it worked but something else happened as well. when jumping to another location in video it gets lagged for .5 sec or so.its not that big of bug but still annoying ,and it didnt happen with alsa.

btw , i heard many bad things about pulse,and i thought it was not a mature audio structure for linux.and i used alsa very easily in suse with smplayer ,so why not in ubuntu?

and again thanks for reply?(you are the *mplayer packager in launchpad?)

---

### Post by delcypher on 2009-11-13
Same problem here.

---

