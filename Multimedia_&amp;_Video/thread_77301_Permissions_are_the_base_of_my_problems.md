---
title: "Permissions are the base of my problems"
date: 2005-10-16
forum: Multimedia &amp; Video
---

### Post by psiko on 2005-10-16
I had both problems about video and audio. I guess the problems about the drm were problems about permissions of the devices. /dev/dri/* must be chmod'ed to 666. First I did what I explained in [this post]("http://ubuntuforums.org/showthread.php?t=76923"). Now I have the changes permanent with udev rules changing the line > SUBSYSTEM=="drm",       GROUP="video" MODE="0666"**in file /etc/udev/rules.d/020_permissions.rules**. 

Now I tested if my sound problem was also about permissions. Yes, it was about it. :o 

computing is as empirical as natural science :???: .

---

