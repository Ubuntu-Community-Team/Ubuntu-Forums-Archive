---
title: "Triplehead - Three monitors on 2 video cards"
date: 2011-07-24
forum: Multimedia Software
---

### Post by lumapu on 2011-07-24
Hi,

the last days I tried to run all my three monitors on 2 videocards. I have read some threads in different formus about configuring xorg.conf with multiple monitors.
I hava attached my current xorg.conf.

Problem:
The monitors which are connected to the first video card are spaning one desktop. On the third monitor there is an own desktop. I can't work with that configuration because I can't drag a window to the third monitor. (see overview.bmp)
If I start Firefox on the third monitor, all is normaly. When I start Firefox on the other monitors, I get a message that allready one instance of Firefox ist started.

The most of the threads including this comando in their xorg.conf file
Option "Xinerama" "true"
There are various comandos with "true", "1" or nothing. If I put this line into my xorg.conf then x don't starts.

Thanks,
lumapu

---

