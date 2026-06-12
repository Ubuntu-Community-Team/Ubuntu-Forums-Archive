---
title: "Kubuntu Edgy, Xorg 7.1.1, fglrx 8.30.3 no accelr..."
date: 2006-11-13
forum: Multimedia &amp; Video
---

### Post by Xemanth on 2006-11-13
Problem is that in Kubuntu Edgy, the newest official fglrc package from ati site 8.30.3 and xorg 7.1.1 doesn't work very well along.

Do you have this kind of problem too? Is it possible that I could hack drivers somehow to ignore that error ](*,)
My hw are: Laptop: Acer Aspire 5024wlmi with AMD(ATI) Mobility X700 128mb.

here are my xorg conf, log and my current kernel config:
[http://xemanth.ath.cx/~xemanth/](http://xemanth.ath.cx/~xemanth/)

----------
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.1.0
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
----------


edit: Ups i have screwed my xorg.conf litle bit
now i got Xv working but same xorg compatibily error which causes direct rendering not to work.
Section "Extensions"
        Option      "Composite" "Disable" <- I had there 0 :)
EndSection

xemanth@5024wlmi:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  156 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  30
  Current serial number in output stream:  30
xemanth@5024wlmi:~

edit2: log files updated in [http://xemanth.ath.cx/~xemanth/](http://xemanth.ath.cx/~xemanth/)
Is this problem in current fglrx drivers or am I just stupid ? :|

---

### Post by Xemanth on 2006-11-14
Problem solved:
I didn't have in xorg.conf Load "dri" :mrgreen:

xemanth@5024wlmi:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
2887 frames in 5.0 seconds = 577.400 FPS
3385 frames in 5.0 seconds = 677.000 FPS
3445 frames in 5.0 seconds = 689.000 FPS
xemanth@5024wlmi:~$

---

