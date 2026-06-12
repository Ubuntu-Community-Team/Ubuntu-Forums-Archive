---
title: "256 color desktop"
date: 2008-10-07
forum: Multimedia Software
---

### Post by horacle2008 on 2008-10-07
hi, Im an old fractint fan from my amiga days (linux beginer) and I just got it for ubuntu (xfractint) but it doesnt play well with a 32 bit deep desktop; it freezes and I have to reboot... Is there a way to set the desktop to 256 colors? I cant find any control for that.

TIA

---

### Post by jpkotta on 2009-01-17
I've never had that kind of trouble with Xfractint.  Some options:

1) Run DOS Fractint in some sort of DOS emulator (slow).

2) Start a Xephyr server with the color depth you need, and tell Xfractint to use that display.  Xephyr is a nested X server.  
```
sudo aptitude install xserver-xephyr
Xephyr :20 -screen 1024x768x8 &
xfractint -display :20 -fixcolors 256 -geometry 1024x768

```

---

