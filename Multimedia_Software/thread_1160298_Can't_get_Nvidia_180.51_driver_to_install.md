---
title: "Can't get Nvidia 180.51 driver to install"
date: 2009-05-15
forum: Multimedia Software
---

### Post by jbumgar on 2009-05-15
I can't get the Nvidia 180.51 drivers to install.  I have followed the directions but when I get in the black screen after killing nome and type in the commands I'm supposed to, nothing happens it seems. The cursor just skips down a line and that is it.  I've made sure that I've typed it in with the proper case.  What am I doing wrong?

I'm typing in sudo NVIDIA-Linux-x86-180.51-pkg1.run

---

### Post by IanW on 2009-05-15
> **jbumgar said:**
> I can't get the Nvidia 180.51 drivers to install.  I have followed the directions but when I get in the black screen after killing nome and type in the commands I'm supposed to, nothing happens it seems. The cursor just skips down a line and that is it.  I've made sure that I've typed it in with the proper case.  What am I doing wrong?

I'm typing in sudo NVIDIA-Linux-x86-180.51-pkg1.run

You should be typing
```

sudo [COLOR="Red"]sh[/COLOR] NVIDIA-Linux-x86-180.51-pkg1.run

```
And anyway, [180.60](http://www.nvnews.net/vbulletin/showthread.php?t=132891) is out.

---

### Post by jbumgar on 2009-05-15
Still does the same thing.

---

