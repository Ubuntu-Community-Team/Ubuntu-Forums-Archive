---
title: "Poor video in 7.10"
date: 2008-01-10
forum: Multimedia &amp; Video
---

### Post by mistrial on 2008-01-10
I have recently upgraded from 7.04 to 7.10 and I am experiencing very poor video quality. In totem the videos are very pixelated, while in VLC they are pixelated and choppy. The same video files were working fine in 7.04. 

I have an ATI Radeon X1650 PRO video card and xorg-driver-fglrx version 7.1.0-8.37.6 installed. Does anyone know how to solve this? Any suggestions are appreciated. Cheers.

---

### Post by mistrial on 2008-01-11
Anyone that can point me in the right direction? Actually any direction would be appreciated... :)

---

### Post by EssGee on 2008-01-14
Have spent a lot of time trying to sort this myself - to no avail yet. :(  So, cannot point you in any specific direction, but hope this helps somewhat.

There has been a lot said in these forums about getting ATI cards to work properly with Linux.  I have been trying various things from below with limited success:

[http://ubuntuforums.org/showthread.php?t=515573&highlight=ati+radeon+x1650+pro](http://ubuntuforums.org/showthread.php?t=515573&highlight=ati+radeon+x1650+pro)

[http://ubuntuforums.org/showthread.php?t=221320&highlight=ati+radeon+x1650+pro](http://ubuntuforums.org/showthread.php?t=221320&highlight=ati+radeon+x1650+pro)

[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

If you can make do without Hardware Acceleration and 3D while you figure this out, edit your /etc/X11/xorg.conf and change the graphics driver in the "Device" section for the graphics card to "vesa".  It may improve your video playback.

---

### Post by mistrial on 2008-01-16
EssGee, thanks for the tips. I  haven't had the chance to try them yet, but I have found a way to improve the video quality. By changing the video output module in VLC from default to OpenGL I get much better video quality. The pixelated edges are gone, however the picture is still choppy from time to time. 

Have you made any revolutionary discoveries over the last few days?

PS: The video output modules is found under Settings->Preferences->Video->Output modules.

---

