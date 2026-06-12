---
title: "sony z switchable graphics: v4l-conf no dga direct video mode for this display"
date: 2010-01-29
forum: Multimedia Software
---

### Post by niffcreature on 2010-01-29
so... i was trying to get my webcam to work on my sony z590, and i couldnt figure out what was going on because its supposed to be supported by default out of the box (at least with opensuse linux) as listed here [http://www.basyskom.org/~eva/log_installation_vaio_z21vnx.html](http://www.basyskom.org/~eva/log_installation_vaio_z21vnx.html)
and i think on the launchpad page as well.
lsusb got Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub which is supposedly correct for my camera. but somewhere i read about the command v4l-conf and tried it getting this: 
using X11 display :0.0
dga: version 2.0
WARNING: No DGA direct video mode for this display.
mode: 1600x900, depth=24, bpp=32, bpl=6400, base=unknown
can't open /dev/video0: No such file or directory

now, v4l isnt just for webcams, right? if i could tell you how i got my nvidia card working i would, but i dont remember except that i edited the grub boot options, loaded the sony-laptop module and i used and application called EnvyNG.
ive been having some other video problems with games in fullscreen making my system crash horribly but only sometimes - saurbraten, however, always. 
anyone know what might be going on here, if this and my webcam are related?
i would appreciate help with EITHER problem :-s
thanks.

---

### Post by niffcreature on 2010-01-29
anyone?

---

### Post by niffcreature on 2010-02-01
help!!!!!
why would a webcam not work when it is supposed to be supported?

---

