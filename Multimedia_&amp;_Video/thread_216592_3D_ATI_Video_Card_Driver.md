---
title: "3D ATI Video Card Driver"
date: 2006-07-15
forum: Multimedia &amp; Video
---

### Post by harys on 2006-07-15
i wanted to activate the 3d video acceleration, and i followed all the instructions on [https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html) and then after launching the command in the terminal i chose almost all the default option. i then restarted the computer and when i issued the command glxinfo | grep rendering i got this result :

harys@harys> glxinfo | grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
harys@harys>

thanks for your help.
harys

---

### Post by Dubbayoo on 2006-07-15
make sure you're loading glx and dri in xorg.conf

---

### Post by Weevil on 2008-03-10
Yeah I had this issue on the pure:dyne distro with my ATI Radeon9800 but this worked (at least for returning some more clear instructional driver errors ;) )

tnx!

---

