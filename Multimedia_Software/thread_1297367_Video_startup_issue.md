---
title: "Video startup issue"
date: 2009-10-21
forum: Multimedia Software
---

### Post by jvoytko on 2009-10-21
Hello everyone.  As you probably see, I'm new.  I've recently fell in love with Linux and have an entire PC dedicated to it.

Back to the point: I installed a video driver for my ATI Rage 128 Pro legacy video card. Now before I installed it, the video worked perfectly. The reason I tried to install the driver is b/c my video card is also a TV tuner. I do not have a TV and want to watch it. Long story on why I want to via my PC... But I cannot boot. When I try to boot, it looks like the ubuntu logo (the symbol + text beside it that says "Ubuntu") is burnt into the screen or like it was a bad attempt at making a fading top border (Only way I can describe it) and it is my only PC at my home. I am doing this running Live CD. Is there a way to restore via the Live CD to the default video driver?

Thank you in advance!!!!!!!!!!!!!!!!!

---

### Post by spiderbatdad on 2009-10-21
To reconfigure your video card you can try the following. Boot into recovery mode from the grub menu. When you get a command prompt, enter
```
dpkg-reconfigure -phigh xserver-xorg
```

---

