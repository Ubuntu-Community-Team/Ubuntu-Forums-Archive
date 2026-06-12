---
title: "Help w/ ATI 9600"
date: 2007-02-09
forum: Multimedia &amp; Video
---

### Post by nomad00 on 2007-02-09
Greetings all! After following the sticky "Howto: Fglrx 8.26.18 Driver Install" above, I still have: 
[INDENT]$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)[/INDENT]

and

[INDENT](II) fglrx(0): Composite extension enabled, disabling direct rendering 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *[/INDENT]

even after adding:

[INDENT]Section "Extensions" 
    Option "Composite" "true"
EndSection[/INDENT]

Anyone have any advice?

---

### Post by bionnaki on 2007-02-10
sudo apt-get install linux-restricted-modules-$(uname -r)

and then add:

> Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection


to xorg.conf 

reboot.

---

### Post by NT4usB on 2007-02-10
Follow the directions and run Alberto's skript. It's a peach.
(Note: when you run it you may have to first uninstall the ATi then install. I did...)

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

ct@wimp:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6286 (8.33.6)

ct@wimp:~$ glxgears -printfps
2488 frames in 5.0 seconds = 497.506 FPS
10019 frames in 5.0 seconds = 2003.779 FPS*
26047 frames in 5.0 seconds = 5209.367 FPS*
2394 frames in 5.0 seconds = 478.800 FPS
2490 frames in 5.0 seconds = 497.625 FPS
2487 frames in 5.0 seconds = 497.388 FPS
2497 frames in 5.0 seconds = 499.023 FPS
2501 frames in 5.0 seconds = 500.186 FPS

---

