---
title: "Framebuffer/Post Grub Console Resolution Slightly Off"
date: 2013-05-05
forum: Multimedia Software
---

### Post by Loafers on 2013-05-05
```
3.2.0-4-amd64 #1 SMP Deiban 3.2.41-2 x86_64 GNU/Linux
00:2.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
```
I just did a fresh install and noticed the framebuffer/tty/post grub console resolution was clipped on the left by a few pixels, which is odd since it is already in its native solution of 1920x1080.

So I did some googling and tried adjusting the [frambuffer resolution](https://wiki.archlinux.org/index.php/GRUB#Setting_the_framebuffer_resolution) and everything in [this thread](http://forums.debian.net/viewtopic.php?f=5&t=41881), but neither worked. 

X resolution does not exhibit this problem either 

Any suggestions :(? (I'll try to upload my /etc/default/grub and /boot/grub/grub.cfg as soon as I get the machine set up).

---

