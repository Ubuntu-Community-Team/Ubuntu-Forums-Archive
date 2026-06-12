---
title: "HOWTO - Enabling Direct Rendering"
date: 2007-08-29
forum: Multimedia &amp; Video
---

### Post by Beggar on 2007-08-29
Problem:
The other day I was playing around and noticed that direct rendering was disabled.
For anyone who cares, Im running Feisty Fawn, on a dell inspiron E1505 with an nvidia geforce go 7300, and I run Beryl as my default window manager.


Information of Interest:
I followed the usual steps of modifying the xorg.conf file, I.E. added the following:

```
Section Module
Load "DRI"
Load "glx"
...
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Videocard0"
driver "nvidia"
Option "AllowGLXWithComposite" "True"
Option "AddARGBGLXVisuals" "True"
Option "RenderAccel" "True"
...
EndSection

```

After restarting X by stopping gdm, then running startx, glxinfo | grep rendering said yes.
After restarting the computer, and later GDM, glxinfo said no direct rendering, wtf?

So after some looking around I noticed that when gdm starts x, it was being put on display :93, and the log file was very different (it looked like everything was being picked up dynamically). However when I ran startx, it was being run on display :0.

Solution:
I edited the /etc/gdm/gdm.conf-custom file and changed the following entry:

```

[server-XGL]
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo

```

to:

```

[server-XGL]
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo

```

and everything worked!

My theory is that it was starting the xgl server on :0, so when it went to start the X server it was being done on another display. Why it doesnt use the xorg.conf file if its not on display :0? Doesnt seem to make sense to me, but whatever, hope this helps someone.

---

