---
title: "New Nvidia FX5200 no glxgears"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by alienexplorers on 2007-02-05
I just installed a Nvidia FX-5200 card in my machine.  I enabled the nvidia-glx drivers and when I try to run glxgears to see the frame rate I get this error:

terminator@terminator-desktop:~$ glxgears -printfps
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
terminator@terminator-desktop:~$


How do I fix this?

---

### Post by taurus on 2007-02-05
How did you install the nvidia driver?  Did you enable it in /etc/X11/xorg.conf?  And did you remember to restart X with <Ctrl><Alt>Backspace?

---

### Post by alienexplorers on 2007-02-05
Installed drivers via Automatix2 and forgot to restart X.  Did a full reboot and everything is running OK now.  GLXGEARS is running at 1300-1350 so all seems OK now.

---

