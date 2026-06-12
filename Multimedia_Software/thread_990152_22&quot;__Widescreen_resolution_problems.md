---
title: "22&quot;  Widescreen resolution problems"
date: 2008-11-22
forum: Multimedia Software
---

### Post by vj83 on 2008-11-22
I have a 22" Envision widescreen monitor which supports a max resolution of 1680x1050. I have an intel 845GL card with the driver package xserver-xorg-video-intel installed. 

The problem is that while the "screen resolution" is claimed to be 1680x1050 by ubuntu, the actual display is not sharp and is very edgy. I can fix this problem temporarily (each time I boot) by either
1. switching the resolution to 1280x1024 and then switching it back, or
2. Running displayconfig-gtk and having the program test the current resolution. After running the test, the display is fine.

Is there a permanent fix to this? Thanks.

---

### Post by wolfen69 on 2008-11-22
in terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then restart x or reboot. hope this works for you.

---

### Post by vj83 on 2008-11-22
Nope. It doesn't fix the problem. In fact when I do the usual switch resolution trick I mentioned earlier and then type  
sudo dpkg-reconfigure -phigh xserver-xorg
and restart x, it returns to its fuzzy and edgy resolution. Any other ideas?

---

