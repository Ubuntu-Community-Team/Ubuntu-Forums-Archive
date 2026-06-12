---
title: "Screensavers Missing"
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by phaedo5 on 2007-03-12
Hello. I have Edgy Eft installed, running gnome.

When I look at my screensavers, only a few of them show up and work. The more simple ones seem to do ok. I have a nvidia card. I am pretty sure its installed correctly. My xorg.conf says "nvidia" in the driver section.

I don't understand why I can't see a lot of my screensavers. What is the issue? Any help would be great.

>>>>

Ok. It says this, which is clearly not what I want to see - I'm guessing.

justin@xUbuntu:~$ glxinfo
name of display: :0.0
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

visual x bf lv rg d st colorbuffer ax dp st accumbuffer ms cav
id dep cl sp sz l ci b ro r g b a bf th cl r g b a ns b eat
----------------------------------------------------------------------
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
0x21 24 tc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
0x22 24 dc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 0 0 None


Where do I go from here?

My xorg.conf file says this:

Section "Device"
Identifier "Generic Video Card"
Driver "nvidia"
BusID "PCI:3:0:0"
EndSection

Not good?

---

