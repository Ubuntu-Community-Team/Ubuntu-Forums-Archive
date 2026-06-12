---
title: "Monitor resolution in remote logings"
date: 2006-11-21
forum: Multimedia &amp; Video
---

### Post by angel6700 on 2006-11-21
Hello,

I have 2 computers connected with Ethernet. One is running kubuntu 6.10 and the other, which is old, is running debian with a minimal package set to have the xserver.

I have properly configured the xorg.conf file in the debian machine, and can start the window manager icewm, in a correct way. I prefer resolution 1024x768 and a refresh rate of 75Hz, so I have the modeline in the section monitor, and a modes in the screen section making use of it. So here all works fine.

I want to connect to the X session of the ubuntu machine (which is accepting xdmcp queries) with the debian host, so I have tried two different ways (I think both are the same):
1. CTRL-ALT-F1; stop the desktop manager; and X -query ubuntuXserver.
2. If the desktop manager is kdm or gdm (in debian), is easy to select a chooser of xdmcp servers where I just have to click in the ubuntuXhost.

Ok, it works, also but here comes my problem: When I login in the remote server, the resolution change, and also does the refresh rate. I do not know why. Because in the xorg.conf of the machine, it is just write to use one mode, and is ok when working locally.

Also, as a secondary behavior, when i move the mouse, (using the remote connection) quite a lot of "noise" appears in the monitor, like horizontal lines, mainly in the left part of the screen. Probably this is a consequence of the first problem...


So, please, can anybody help me with this? thank you all ;)

Just for information: (hardware info)

Ubuntu machine:
  nvidia nv17, geforce4 mx 64MB
  monitor plilips 107s (1024x768@85)
  driver nvidia from the ubuntu repos (restricted modules)

Debian machine:
  s3virge dx 2MB
  monitor HP72 (1024x768@75)
  driver s3virge from xorg.


chao.

---

### Post by angel6700 on 2006-11-22
Nobody knows the reason of this?

Probably, I am not searching in the correct way, but I cannot find information about it.

Thanks again.

---

### Post by angel6700 on 2006-11-26
Please, some ideas?

Somebody told me that there is a place to specify the resolution for remote comections by xdmcp, but I have read the files in /etc/kde3/* and didn't find were.

Thanks.

---

### Post by halfvolle melk on 2006-11-26
Maybe you could use xrandr to set another resolution, I'm not sure. Or maybe you could look into FreeNX as an alternative.

---

### Post by angel6700 on 2006-11-26
Thankyou,

yes, with xrandr I can change to a refresh rate of 75 Hz. And this avoid the noise in the screen.

---

