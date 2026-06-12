---
title: "X config on ST5020 Tablet - 9.04 upgrade"
date: 2009-08-10
forum: Multimedia Software
---

### Post by vanwall on 2009-08-10
Hello, I have a Fujitsu ST5020 tablet pc that I was running with U8.04.  I had to run with keyboard & mouse.  I saw that 9.04 supported Wacom tablets, so I tried a Live CD and it worked with the pen!  I then started the upgrade path, 8.04 to 8.10, 8.10 to 9.04.  Whenever I boot 9.04, the screen breaks up and then Ubuntu goes to a default 800x640 mode.  I tried to run the auto config, with no better results.
 
My question is this, When I run the Live CD, where are the X configuration files kept.  I looked in /etc/X11/xorg.conf, but all it contained was the barest of simple configs.  Where is the config that is running the Live Ubuntu 9.04?

---

### Post by Favux on 2009-08-10
Hi vanwall,

Welcome to Ubuntu forums!

In Jaunty the Wacom stuff is configured through HAL/.fdi.  HAL = Hardware Abstraction Layer & .fdi = device information file

The '10-wacom.fdi' is located at "/usr/share/hal/fdi/policy/20thirdparty/".

The xorg.conf is being deprecated.  Which is why it seems "empty".  The problem you're having sounds like a video problem.  You may need to change something in your video entries.  Jaunty has trouble with some video cards notably some Intel integrated chipsets.  If you know what your video is you could look into that.

---

### Post by vanwall on 2009-08-11
Thank you, I'll look into HAl.  The 9.04 Live CD has no problem with the video driver settings, that's why I was surprised that 9.04 upgrade was not working.

---

### Post by vanwall on 2009-08-12
I copied xorg.conf from LiveCD U9.04 to u9.04 on HD.  Rebooted and video is OK and Pen works.  Thanks!

---

### Post by Favux on 2009-08-12
Hi vanwall,

Great!  Good job.

If you need help fine tuning Wacom let me know.

---

