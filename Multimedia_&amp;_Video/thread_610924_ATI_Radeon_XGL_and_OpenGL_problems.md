---
title: "ATI Radeon XGL and OpenGL problems"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by skychris on 2007-11-12
Hi everyone,

I've been on it for almost a week now, and here's the trick, in Terminal, during the setup of my driver, I had to follow the lines bellow, because I didn't have the same setting showing by using  "fglrxinfo" or "glxinfo"
but look what I found...

> chris@chris-laptop:~$ glxinfo|grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
chris@chris-laptop:~$ aticonfig --query-monitor
  Connected monitors: none
  Enabled monitors: none
chris@chris-laptop:~$ export DISPLAY=:0
chris@chris-laptop:~$ aticonfig --query-monitor
  Connected monitors: lvds
  Enabled monitors: lvds
chris@chris-laptop:~$ glxinfo|grep direct
direct rendering: Yes
chris@chris-laptop:~$ 


it does what I want, meaning setting the OpenGL settings showing with the "glxinfo" to the ATI card, but when I close the Terminal window, it goes back as before, giving the OpenGL to Mesa  arghhhh:confused:

any idea on how to keep the right settings once and for all

](*,)

---

### Post by Yellow Pasque on 2007-11-13
Post your /etc/X11/xorg.conf

---

