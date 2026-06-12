---
title: "Frontend doesn't seem to start from mythwelcome (doesn't get drawn)"
date: 2011-11-01
forum: Mythbuntu
---

### Post by lauri.korpela on 2011-11-01
Hello,

I have new hardware (AMD A6 3650 with Asus F1A75-M PRO) and a fresh install of Mythbuntu 11.04 upgraded to 11.10. I have latest updates from mythtv 0.24 branch and also latest proprietary drivers from AMD (11.10).

The problem is that when I try to start frontend from mythwelcome nothing happens. I have found that switching to other terminal (ctrl+alt+f1) and back to graphical one (ctrl+alt+f7) makes the frontend visible. It seems that frontend starts normaly, but doesn't get drawn properly or the screen doesn't get updated.

This occurs also in mythbackend setup. Selecting something from the main menu doesn't seem to work. But after switching to other tty and back, the selected menu is visible.

Switching between programs with alt+tab doesn't do anything.

I'm little bit clueless at the moment where to start fixing this.

Best regards,
-Lauri

---

### Post by musici8 on 2012-09-12
If you haven't solved already, I was experiencing this issue as well. My fix was found on the following page:

[http://www.mythtv.org/wiki/ATI_Proprietary_Driver#Garbled_Screens_with_OpenGL_Painter]("http://www.mythtv.org/wiki/ATI_Proprietary_Driver#Garbled_Screens_with_OpenGL_Painter")

Insert the following into a startup script so that it is run before mythfrontend:

export LIBGL_ALWAYS_INDIRECT=true

---

