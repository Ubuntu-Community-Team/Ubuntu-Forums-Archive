---
title: "nvidia not working for GeForce 7500 LE in 8.10"
date: 2008-11-18
forum: Multimedia Software
---

### Post by jcline on 2008-11-18
I have installed Ubuntu 8.10 and cannot get nvidia driver to
work for my GeForce 7500 LE card.  I get the following error
message from X.org.log.  Could anyone who has gotten this card to work post their Xorg.conf, and version of the nvidia driver package they are using?  thanks!

(==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
(EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):     additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

---

### Post by eternalnewbee on 2008-11-18
I found this:
[http://packages.ubuntu.com/intrepid/nvidia-glx-177](http://packages.ubuntu.com/intrepid/nvidia-glx-177)
Hope this helps. Be back in a couple of hours, and will check if you've made any progress.
Good luck.

---

### Post by jcline on 2008-11-18
Thanks, but I do not see any useful information there, aside from the fact that my device is supposed to be supported.  However nvidia-xconfig does not seem to be creating the right
xorg.conf file.

Does anyone know which README file the Xorg.log error message is referring to when it says to look at the README for common problems?

---

