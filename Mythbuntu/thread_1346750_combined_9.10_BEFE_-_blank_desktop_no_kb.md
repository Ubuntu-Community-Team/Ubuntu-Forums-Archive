---
title: "combined 9.10 BE/FE - blank desktop no kb"
date: 2009-12-05
forum: Mythbuntu
---

### Post by elj4176 on 2009-12-05
long time myth user but this is the first time I have had this issue. I recently upgraded to 9.10 using ssh from another machine. The BE/FE has been a headless machine for awhile so this problem could have nothing to do with the upgrade.
I hooked up a projector to the vga (had worked previously) and all i have is a black/blank desktop. While rebooting I see the usual startup messages and the mythbuntu logo comes up and then all goes black and my kb quits working. 
The backend is still running and I can run mythfrontend from my other machines just fine.I can vnc into the BE/FE and the desktop is there but I cannot start mythfrontend.
The BE/FE has onboard intel video chipset. I can go buy a new video card but I'd rather not.
When I run mythfrontend from the ssh session I get:
xprop:  unable to open display ''
mythfrontend.real: cannot connect to X server 
I know I cannot run the frontend from ssh but the error may be useful.

Any ideas? Thanks!
edited to add:

when I try to run the frontend from the cli I get this error:
2009-12-05 20:40:24.600 Using the OpenGL painter
QGLContext::makeCurrent(): Cannot make invalid context current.
Segmentation fault

solution:
ran ssh -X and set the themepainter back to QT by:
mythfrontend -O ThemePainter=qt
I was then able to run the FE on the BE/FE over ssh and change the theme painter.

---

