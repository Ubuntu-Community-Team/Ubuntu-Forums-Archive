---
title: "Volume Randomly Changing Produces Clicking Sound"
date: 2013-04-24
forum: Multimedia Software
---

### Post by agoessling on 2013-04-24
I have a problem where my volume randomly glitches and this produces and audible clicking sound about every ~10sec. I can actually watch the volume indicator jitter when this happens. I am using a Intel® Core™ i7-3770K with integrated graphics and audio, and this problem only occurs with with something connected to the motherboard line out (not with the front line out). Here is my ALSA report:


[http://www.alsa-project.org/db/?f=3370377ecaaf9f9e4f9c3b82691c5aeba5088d41](http://www.alsa-project.org/db/?f=3370377ecaaf9f9e4f9c3b82691c5aeba5088d41)


I have seen other posts about this problem**, but there solutions seemed to rather hardware specific, so I didn't want to blindly down that path. Can someone point me to a relevant solution, or let me know what I need to do to debug this?
**
[http://ubuntuforums.org/showthread.php?t=1658911](http://ubuntuforums.org/showthread.php?t=1658911)
[http://ubuntuforums.org/showthread.php?t=1525970](http://ubuntuforums.org/showthread.php?t=1525970)
[http://ubuntuforums.org/showthread.php?t=1658911](http://ubuntuforums.org/showthread.php?t=1658911)

---

### Post by agoessling on 2013-04-24
[h=1][COLOR=#333333][FONT=Ubuntu]So I have been just trying random things from forum posts, and this has seemed to fix it:[/FONT][/COLOR][/h][COLOR=#333333][FONT=Ubuntu]Adding
options snd-hda-intel model=generic
to
/etc/modprobe.d/alsa-base.conf[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Although I think I might have given up functionality because I now see far less options in the sound settings. Any idea about the root cause?[/FONT][/COLOR]

---

