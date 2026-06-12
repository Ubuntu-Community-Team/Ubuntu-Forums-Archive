---
title: "[SOLVED] No video working on Gutsy (configuration: dual monitor, Intel 915GM graphics"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by arrizaba on 2007-11-27
Since I installed Gutsy It seems that every time that I try to start a video file (either from VLC, Mplayer, Totem,....) or load a webpage on firefox with a flash-based video, the playing program freezes and forces me to quit.

Has anyone experience similar problems? Does anyone have an idea how to solve this? (I have browsed through the forums without finding any solution.... :( )

[COLOR="Red"]More info:[/COLOR] I have a Dell Inspiron 1300 connected to an external monitor (with the laptop screen disabled) and using a Intel 915GM graphics card with the i810 Intel driver.

---

### Post by arrizaba on 2007-11-27
I now realize that any program that outputs sound experiences the same freezes.

I managed to get VLC playing video by changing the video output from XV to X11. However, videos start without sound and the program still freezes....

This leads me to think that the freezes occur because of the sound. Any help here?

---

### Post by arrizaba on 2007-11-27
OK. It seems I managed to fix my own problems... :)

Indeed, the problem was related to the sound.

I followed the hints from:

[http://ubuntuforums.org/showthread.php?p=3849697#post3849697]("http://ubuntuforums.org/showthread.php?p=3849697#post3849697")

And the video/audio players stopped freezing.

---

