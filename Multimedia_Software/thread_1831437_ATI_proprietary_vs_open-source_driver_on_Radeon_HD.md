---
title: "ATI proprietary vs open-source driver on Radeon HD 5xxx"
date: 2011-08-23
forum: Multimedia Software
---

### Post by marin123 on 2011-08-23
Hello!

I have ATI Radeon HD 5650 (code name Redwood) on Ubuntu 11.04. And I have been experimenting with open-source and proprietary driver.

The problem with proprietary driver is bad 2D rendering when watching movies in VLC (and any other), because if vsync is off, video is tearing and when its on, the video seems to stutter (the background moves in steps, not smooth). I have tried open-source radeon driver and its far better, but that driver doesn't have 3D acceleration for playing games. I was trying to play Hive Rise, and with proprietary driver works great, but with open-source the game starts, but i don't see the interface (start game, options, etc.).

It seems that Mesa 7.10 (in Natty) doesn't have 3D support for this card, but Mesa 7.11 (in Oneiric) will have that. Is that correct? I just want to have good 2D performance with ability to play games.

Thanks! :)

---

### Post by handy on 2011-08-23
You could try upgrading both the kernel & the associated AMD/ATi driver stack. This is reliable & quite easy to do, there is a how-to in the Ubuntu Stuff: part of the first post here:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

---

### Post by marin123 on 2011-08-23
Thank you for your reply...
I have looked at the link you posted and saw that radeon driver for my card doesn't have hdmi audio, and that's very important to me, so I'll just sit back and wait until they do that :)
I hope they will do it until 11.10.

---

### Post by handy on 2011-08-23
I'm sure that it is coming, as that kind of thing has become so popular these days. :)

---

