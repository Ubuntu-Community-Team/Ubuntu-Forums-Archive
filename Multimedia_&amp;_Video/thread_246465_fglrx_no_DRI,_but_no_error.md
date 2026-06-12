---
title: "fglrx: no DRI, but no error"
date: 2006-08-29
forum: Multimedia &amp; Video
---

### Post by fiete on 2006-08-29
Hi!

I'm trying to get my brother's Radeon 9700 Pro running with DRI.
The problem is, that I do not have direct rendering whenever I start a gnome-session via gdm. When I start gnome directly by startx, everything is fine.

[my /var/log/Xorg.0.log]("http://www.ubuntuusers.de/paste/3236/")
[my /etc/X11/xorg.conf]("http://www.ubuntuusers.de/paste/3237/")

This is obviously some kind of permission problem.

Any idea to solve this is welcome.

Thanks in advance,
Florian

---

### Post by fiete on 2006-09-01
I finally found a solution to my problem. Whenever gdm starts a X-client it also runs /etc/X11/Xsession, which runs all scripts in /etc/X11/Xsession.d/. Among those scripts is /etc/X11/Xsession.d/10fglrx in which I commented the follwing lines:
```

#LIBGL_DRIVERS_PATH=/usr/X11R6/lib/modules/dri
#export LIBGL_DRIVERS_PATH

```
I really do not know what this variable is good for. Anyway, I finally have 3d acceleration :-).

Florian

---

