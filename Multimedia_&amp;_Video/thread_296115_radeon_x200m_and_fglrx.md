---
title: "radeon x200m and fglrx"
date: 2006-11-09
forum: Multimedia &amp; Video
---

### Post by francescob on 2006-11-09
Hello, i've installed the newest ati drivers following the guide from [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
they install fine but doing fglrxinfo gives:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

so, i added these lines to xorg.conf:
Section "Extensions"
        Option      "Composite" "0"
EndSection

as reported in the guide, but now x won't start anymore, i have a  dark screen, and no errors on X log file.
Any hint on this?
thank you
francesco

---

### Post by Melcar on 2006-11-09
Rebuild your xserver...
[http://www.ubuntuforums.org/showthread.php?t=187177&highlight=xserver+defaults]("http://www.ubuntuforums.org/showthread.php?t=187177&highlight=xserver+defaults")
...then re-install the driver following the guide exactly (use step 2), step by step (by the way, it's "Composite" "Disable" not "Composite" "0").

---

### Post by yorik on 2006-11-10
The message from fglrxinfo is telling you that the running opengl driver is mesa (generic one) and not fglrx. Probably your driver is not installed correctly. I reinstalled mine two days ago (ati driver 8.30) following the method described here: 

[http://wiki.cchtml.com/index.php/Ubuntu]("http://wiki.cchtml.com/index.php/Ubuntu")

I think you should remove the driver you installed (if you installed the .deb files, they will appear in synaptic, search for fglrx) and do the procedure again.

---

