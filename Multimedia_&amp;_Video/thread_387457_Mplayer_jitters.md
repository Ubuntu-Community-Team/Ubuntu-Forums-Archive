---
title: "Mplayer jitters"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by becominglumberg on 2007-03-18
I have followed Kliz's tutorial for installing firefox32 on a fresh install of edgy x64, along with all the plugins that make the internet fun.

Currently, when Mplayer tries to fire off a video, it will load, and then repeatedly display that it is playing 'mms:// yatta yatta yatta' and 'http:// yatta yatta yatta'. This will repeat back and forth, over and over. This happens with every test video I try to run. The videos on cnn.com's homepage are a good example.

Any ideas? I have this working normally (via automatix) on my old 32 box, but I would really like to use the 64 edition if possible.

Thanks,
Guy

---

### Post by klytu on 2007-03-18
> **becominglumberg said:**
> I have followed Kliz's tutorial for installing firefox32 on a fresh install of edgy x64, along with all the plugins that make the internet fun.

Currently, when Mplayer tries to fire off a video, it will load, and then repeatedly display that it is playing 'mms:// yatta yatta yatta' and 'http:// yatta yatta yatta'. This will repeat back and forth, over and over. This happens with every test video I try to run. The videos on cnn.com's homepage are a good example.

Any ideas? I have this working normally (via automatix) on my old 32 box, but I would really like to use the 64 edition if possible.

Thanks,
Guy

A number of other folks have reported the same issue with CNN, and I haven't seen a consistent solution that works for everyone. I duplicated that same problem on my Dapper box running Firefox and Mplayer. Tried it under Kubuntu and with Firefox and Mplayer and sometimes I could watch the CNN videos, sometimes the same problem would occur. Note this doesn't happen to me with all videos; most videos play for me without difficulty. I just thought you might try something that works for me sometimes with specifically CNN videos. 

A weird workaround under Dapper that works for me most of the time: while the video is beginning to load, if I switch Mplayer to fullscreen mode the CNN video starts to play normally almost every time! I can then switch back out of full screen mode and the CNN video continues to play. I have to repeat this process each time I load a new CNN video. I haven't been able to get this to work in a tabbed CNN window (I tried while typing this response). I'll post back if I ever figure out why in the world this works!

---

### Post by becominglumberg on 2007-03-19
Thanks. Can I assume that you are running x64?

---

### Post by klytu on 2007-03-19
> **becominglumberg said:**
> Thanks. Can I assume that you are running x64?

I am running the most current kernel in the Dapper repos on a 400 MHz Pentium II machine.

---

