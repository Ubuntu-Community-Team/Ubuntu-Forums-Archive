---
title: "problem with xserver-xorg-driver-i810 version"
date: 2006-10-06
forum: Multimedia &amp; Video
---

### Post by romaluca on 2006-10-06
I have problem with direct rendering:
romaluca@romaluca:~$ glxinfo
name of display: :0.0
i915 DRI driver expected DDX version 1-1.5.x but got version 1.4.1
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
display: :0  screen: 0
direct rendering: No


In past i have installed aiglx and i have removed it.
How i can to set the direct rendering in yes?
Thanks

---

### Post by DarkN00b on 2006-10-06
I had this exact problem. I had to restore a working backup copy of my /etc/X11/xorg.conf and my /etc/gdm/gdm.conf-custom files. Everything worked fine after that. I'm using the same driver as you.

ou might also go [here]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX") and remove the parts of those files which are changed.  Sort of do it in reverse.

---

