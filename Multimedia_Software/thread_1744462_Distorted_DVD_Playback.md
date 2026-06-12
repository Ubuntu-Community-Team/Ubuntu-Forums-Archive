---
title: "Distorted DVD Playback"
date: 2011-04-30
forum: Multimedia Software
---

### Post by gattz on 2011-04-30
I'm experiencing some distorted playback when I try to watch a DVD. The only way I can describe it is that the video is completely distorted and unwatchable. There are lines that kind of look like static all over and green bars flicker in and out. The video kind of skips too. The weird thing is that it doesn't begin until I pick an episode from the menu.

Any help is appreciated.

---

### Post by xcrunner78 on 2011-08-27
bump

---

### Post by thewolfman on 2011-08-28
If you haven't done it already, try installing "medibuntu" repo:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Once you have done that and you have reloaded your software list, make sure that you have "libdvdcss2" and "non-free-codecs", also if you haven't already done it, download the drivers for your graphics card which you can download via the control center > "additional drivers".

Hope this helps you guys.

Regards thewolfman:P

---

### Post by xcrunner78 on 2011-08-28
I just figured it out.  I had the mediubuntu, but it was the xorg-edger ppa that was causing the problem.  I ran a ppa purge on it and it is fixed.  Thanks anyway!

---

