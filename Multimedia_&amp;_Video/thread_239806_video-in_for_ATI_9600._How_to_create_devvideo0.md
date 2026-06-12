---
title: "video-in for ATI 9600. How to create /dev/video0?"
date: 2006-08-19
forum: Multimedia &amp; Video
---

### Post by gizban on 2006-08-19
I want to be able to get video-in to work with my ATI All-in-Wonder 9600 card.  I tried GATOS, but that didn't work. The forums suggested tvtime and xawtv. But for those to work, I need /dev/video0. When I run tvtime, it says it can't find /dev/video0 (which doesn't exist). When I run xawtv, the screen goes black and I need to reboot.  When I run v4l-conf, the screen goes black and I need to reboot.  Does anyone know how to create /dev/video0?

My card is an ATI ALl-in-Wonder 9600.  I already installed the video drivers for it. (I can run openGL apps at full speed).

When the screen goes black, I can press ctrl-alt-F1, but how do I get back into Gnome without having to reboot?

---

### Post by Blixter on 2006-10-30
> **gizban said:**
> I want to be able to get video-in to work with my ATI All-in-Wonder 9600 card.  I tried GATOS, but that didn't work. The forums suggested tvtime and xawtv. But for those to work, I need /dev/video0. When I run tvtime, it says it can't find /dev/video0 (which doesn't exist). When I run xawtv, the screen goes black and I need to reboot.  When I run v4l-conf, the screen goes black and I need to reboot.  Does anyone know how to create /dev/video0?

My card is an ATI ALl-in-Wonder 9600.  I already installed the video drivers for it. (I can run openGL apps at full speed).

When the screen goes black, I can press ctrl-alt-F1, but how do I get back into Gnome without having to reboot?

try this one. It work for me:

**tvtime --device=/dev/video1 -S**

---

### Post by CarpKing on 2006-10-30
ATI's fglrx driver does not support video-in.  Can you run Ubuntu without fglrx (I haven't been able to since Breezy, but I'm working on it).  If you can, you might be able to get video capture using the open-source radeon driver.  Take a look at these threads:

[http://www.ubuntuforums.org/showthread.php?t=273291&highlight=ati+capture](http://www.ubuntuforums.org/showthread.php?t=273291&highlight=ati+capture)
[http://www.ubuntuforums.org/showthread.php?t=275831&highlight=ati+capture](http://www.ubuntuforums.org/showthread.php?t=275831&highlight=ati+capture)
[http://www.ubuntuforums.org/showthread.php?t=238511&highlight=ati+capture](http://www.ubuntuforums.org/showthread.php?t=238511&highlight=ati+capture)

Then maybe join us in this thread, where we are trying to figure out if it is truly possible: 
[http://www.ubuntuforums.org/showthread.php?t=283010&highlight=ati+capture](http://www.ubuntuforums.org/showthread.php?t=283010&highlight=ati+capture)

---

