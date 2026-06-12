---
title: "NVidia AND Intel graphics"
date: 2011-10-05
forum: Multimedia Software
---

### Post by aphylius on 2011-10-05
Hi people,

I have this major problem with my ASUS N55S laptop.
This system has an Intel graphics card as well as a NVidia card. They do this to reduce power consumption when running on battery.

This is how it shows in lspci:
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 1247 (rev a1)

glxinfo shows:
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

And there is no way to disable the intel card, while I want NVidia because the performance of the Intel card sucks. I can't even run Compiz right now.

I tried to disable it in the BIOS but there is no option to do this.

Anyone have any ideas?
It would be greatly appreciated.

---

### Post by lcman on 2011-10-05
> **aphylius said:**
> Hi people,

I have this major problem with my ASUS N55S laptop.
This system has an Intel graphics card as well as a NVidia card. They do this to reduce power consumption when running on battery.

This is how it shows in lspci:
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 1247 (rev a1)

glxinfo shows:
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

And there is no way to disable the intel card, while I want NVidia because the performance of the Intel card sucks. I can't even run Compiz right now.

I tried to disable it in the BIOS but there is no option to do this.

Anyone have any ideas?
It would be greatly appreciated.

Install nvidia drivers from the Additional Drivers. Then, edit /etc/X11/xorg.conf and comment out all non-glx modules. Reboot.

---

### Post by beew on 2011-10-05
You have an Optimus enabled laptop. The Nvidia card becomes a kind of hybrid in the Optimus settings so the Nvidia driver for Linux would not work even though it supports the card when it is on its own.  At this point your best bet is probably bumblebee or ironhide (which is a fork of bumblebee by its original creator).

[https://launchpad.net/~bumblebee]("https://launchpad.net/%7Ebumblebee")

A tutorial for ironhide.

[http://community.linuxmint.com/tutorial/view/610](http://community.linuxmint.com/tutorial/view/610)

---

### Post by aphylius on 2011-10-06
beew: that was it :D

I installed ironhide as you said, and now it just works. 
No configuration no tweaking, it works out of the box

Thanks

---

### Post by HellesAngel on 2011-10-06
Yes, Bumblebee did the trick for me too (ASUS X53S).  When the bumblebee configuration asks you for a named configuration to choose I used the K53 configuration from Thomas Kratz as recommended elsewhere and it works fine.

---

### Post by HellesAngel on 2011-10-06
Yes, Bumblebee did the trick for me too (ASUS X53S).  When the bumblebee configuration asks you for a named configuration to choose I used the K53 configuration from Thomas Kratz as recommended elsewhere and it works fine.

---

