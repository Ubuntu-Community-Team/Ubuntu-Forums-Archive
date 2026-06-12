---
title: "GLX for Dell 1420N running Intel drivers"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by teich on 2007-12-25
Hi all,

I'm having problems getting glx direct rendering running on a Dell 1420N with an Intel GMA 3000.  First, a misc. question.  Why does lspci give the following if I have a GMA 3000 (as it states on the spec sheet).

> 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)


Now, on to the real problem.  Anything that uses GLX crashes gdm and I end up at the login screen.  This includes googleearth, glxgears, screensaver previews, etc.  Here's some relevant info.

> 
alex@kookaburra:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect


I'm loading the glx module:
> 
alex@kookaburra:~$ grep glx /etc/X11/xorg.conf
        Load            "glx"


And I'm using the intel driver:
> 
alex@kookaburra:~$ grep Driver /etc/X11/xorg.conf
        Driver          "kbd"
        Driver          "mouse"
        Driver          "synaptics"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "intel"


So, any ideas how I can get programs that use GLX to run?

Thanks.
teich

---

### Post by teich on 2007-12-26
Anyone?  Thanks.

---

### Post by teich on 2007-12-26
Also - I've tried the i810 drivers (specifically by editing the xorg.conf file, replacing the Driver  "intel" line with  Driver "i810") but these are no good.  On boot up I get a warning about "low graphics mode" or something to that effect, lots of screen artifacts, failed compiz, and general instability.

---

