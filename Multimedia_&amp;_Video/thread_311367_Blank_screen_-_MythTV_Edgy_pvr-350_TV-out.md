---
title: "Blank screen - MythTV Edgy pvr-350 TV-out"
date: 2006-12-02
forum: Multimedia &amp; Video
---

### Post by dawson64 on 2006-12-02
I'm a newbie and have been seting up MythTV 0.20 on Edgy with a pvr-350.  I have used Trubblelmaker's how to along with the frontend/backend for edgy.  

I believe the TV out is working properly because i can get it to output the color bars on the TV.  But when i boot up using X server fails.  The slot is 00:15:00.  When i run cat /proc/fb
i have never had anyting come back.  I think my problem has to do with not getting the /proc/fb back.

I have attached some of the log below.

> X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux ubuntu 2.6.17-10-server #2 SMP (==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "TV Screen" (0)
(**) |   |-->Monitor "NTSC Monitor"
(**) |   |-->Device "Hauppauge PVR 350 iTVC15 Framebuffer"
(II) v4l driver for Video4Linux
(II) IVTVDEV_TST: driver for framebuffer: PVR-350
(II) Primary Device is: PCI 01:00:0
(--) Chipset PVR-350 found
(EE) open /dev/fb0: No such device
(EE) Screen 0 deleted because of no matching config section.
(II) UnloadModule: "ivtvdev"
(EE) Device(s) detected, but none match those in the config file.

Fatal server error:
no screens found


Thanks in advance for your help!

---

