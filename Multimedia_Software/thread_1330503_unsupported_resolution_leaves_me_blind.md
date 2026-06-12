---
title: "unsupported resolution leaves me blind"
date: 2009-11-18
forum: Multimedia Software
---

### Post by nategerr on 2009-11-18
I was messing around with my display resolutions and selected an usupported format (16/10 75hertz). the screen went blank but never returned to my previous configuration as it usually does without confirmation. now my nachine boots up but with no video at all after the splash screen so I'm blind and unable to adjust anything. is there a safe mode I can access at startup which will at least give me a terminal? what should I type as a command to get a resolution I can work with?
Thanks in advance
Nategerr

---

### Post by ilil on 2009-11-19
Try to press Ctrl+Alt+F1 or Ctrl+Alt+FN (N=1,2,..7) then you goto terminal

---

### Post by nategerr on 2009-11-26
ok, got to the terminal screen. Now forgive me, but what do I type once there to get a simple screen resolution so I can access my display configuration?

---

### Post by ilil on 2009-11-26
Well, you can try to configure resolution so (choose the right one):
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by ilil on 2009-11-26
Also, you can use xrandr to change [resolution on the fly](http://wiki.ubuntu.com/X/Config/Resolution). But somehow it works for me only within GUI, not at text terminal (Ctrl+Alt+F1, even with DISPLAY setting)

---

