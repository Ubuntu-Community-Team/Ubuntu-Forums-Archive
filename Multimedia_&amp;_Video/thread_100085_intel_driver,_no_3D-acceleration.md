---
title: "intel driver, no 3D-acceleration"
date: 2005-12-06
forum: Multimedia &amp; Video
---

### Post by nalmeth on 2005-12-06
I have a Gigabyte Motherboard, with built in Intel Graphics card, and Intel pentium 4 processor with hyperthreading. Here are model names:
Motherboard: GA-81915ME-GL
Graphics: Intel 82915G express (915gl series)

I have learned that there is a driver that comes with ubuntu for my graphics card called i810. I have reconfigured xserver-xorg to setup with this driver and have dri, glx and GLCore enable (required for 3Daccel).

*glxinfo | grep OpenGL*

This command gives no output, positive or negative. It stalls the terminal, presumably trying to process the output. 

Following help from other folks here, this is  the one step that is out of whack, and as a result, no 3D-acceleration.

attached is the result of *cat /etc/X11/xorg.conf*

thanks for any thoughts..
nalmeth

---

### Post by daller on 2005-12-07
This is from the Hoary-forum, but I think it may help you!

[http://ubuntuforums.org/showthread.php?t=27029](http://ubuntuforums.org/showthread.php?t=27029)

---

