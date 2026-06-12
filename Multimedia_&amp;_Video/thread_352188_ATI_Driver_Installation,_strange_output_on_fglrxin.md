---
title: "ATI Driver Installation, strange output on fglrxinfo"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by DWRZ on 2007-02-03
I followed this guide for installing the ATI Drivers, following method 2. Everything went fine until I got to the "Post-Installation Checks". I executed fglrxinfo and I got the following output:

xxxx@xxxx-Ulysses:~$ sudo fglrxinfo
Password:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

So... is everything right? Is something wrong? What should I do? I'm doing this with the goal of eventually getting Beryl/etc. to work.

EDIT: Also, everything is running very slow now. Games like SuperTux that I used to run with OpenGL on are now very slow with OpenGL on. Planet Racer used to run as well but now it is just very slow...

---

### Post by moffa on 2007-02-03
Since it says Mesa, your driver is not installed properly.  Since you have the 
Xlib: extension "XFree86-DRI" missing on display ":0.0" error you probably tried to install XGL.  I had to use the "ati" driver (the driver you get from ati.com is the fglrx driver) that is the ubuntu default driver to get things working.  Try removing all the fglrx packages and using the xserver-xorg-ati (spelling?) package from synaptic.

Hopefully, that'll fix some of your problems. I've found AIGLX / XGL and fglrx (ati.com's driver) don't work too well.

---

### Post by DWRZ on 2007-02-03
Yeah, I tried (stupidly) to install XGL earlier. I'll try out your suggestions right now.

---

### Post by DWRZ on 2007-02-03
Ok, so I understand that ATI's fglrx isn't good for AIGLX and XGL, and since that's what I want, I need to dump fglrx. I'm a little confused about this though: right now I'm running on GNOME, not XGL, and it gives me this XFree86-DRI Error. When I tried running a session with XGL just now, XGL worked (for the first time) though very slowly. 

Anyway I'll now try removing the package (not sure how but I'll look), then installing Synaptic, and then going on to try AIGLX... 

I'm hoping that will work. :\

---

### Post by DWRZ on 2007-02-03
Ok...wow. I uninstalled ATI, changed some of the xorg.conf settings and all of a sudden AIGLX and Beryl is working. Some things are rather strange though, the cube effect doesn't work at all. Any advice?

---

