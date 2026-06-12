---
title: "[SOLVED] Direct rendering not working on Intel based laptop"
date: 2008-05-17
forum: Multimedia Software
---

### Post by jablan on 2008-05-17
Ok, installed 8.04 from scratch on a laptop with Intel Mobile 945GME graphics.

Everything works fine, except that I can't start Compiz, seems due to direct rendering not working:

> Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX


This is excerpt from glxinfo output:

> jablan@jablan-hp:~$ glxinfo 
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)


Excerpt from /var/log/Xorg.0.log:

> drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed


Any known problems having these symptoms?

---

### Post by jablan on 2008-05-17
It seems to be this problem, I'll try to patch the module and see if it solves it:

[http://ubuntuforums.org/showthread.php?t=766381](http://ubuntuforums.org/showthread.php?t=766381)

Edit: It is, it is! Me happy! :) Solving.

---

