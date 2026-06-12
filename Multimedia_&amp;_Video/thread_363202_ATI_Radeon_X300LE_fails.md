---
title: "ATI Radeon X300LE fails"
date: 2007-02-16
forum: Multimedia &amp; Video
---

### Post by nimy on 2007-02-16
I installed a ATI Radeon X300LE graphics card when my NVIDIA XFX GeForce FX5500 proved defective (streaking problems on both Linux and Windows OS)
The Ubuntu log-on screen is fine, but after log-on, you get only a tiny terminal window - the rest of the screen is dead.  So I  followed Instructions for 6.06 (Dapper) at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
but nothing changed.
  
I then went to [http://ati.de/support/drivers/linux/linux-radeon.html](http://ati.de/support/drivers/linux/linux-radeon.html) and downloaded the Linux installer, ran it, then /usr/bin/aticonfig --initial and the error reads "found fglrx primary device section.  Nothing to do, terminating."  
The output of fglrxinfo was a lot closer to what it should be before I tried running ATI Radeon's install file (ati-driver-installer-8.33.6-x86.x86_64.run), but here goes:
$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

/etc/X11/xorg.conf:
Section "Device"
        Identifier  "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
        Driver      "ati"
        BusID       "PCI:2:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

sudo modprobe fglrx returns nothing, but  lsmod |grep fglrx shows this:
fglrx                 388908  0
agpgart           34888    2 fglrx,via_agp

What to do?

---

