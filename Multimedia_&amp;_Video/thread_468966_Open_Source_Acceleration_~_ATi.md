---
title: "Open Source Acceleration ~ ATi"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by blue_shift on 2007-06-09
Hi

I'm running a radeon 9250 (aka 9200 pro) and kubuntu 7.04.

I'd like to use the open source ATi drivers (which I understand work fully with my card).
However, my xorg.conf file is set to use driver "ati" and I don't get any acceleration.

```
alex@alex-desktop:~$ glxinfo | grep rendering
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No

```

I know there are lots of posts covering this issue for the closed fglrx driver, but I can't find a solution for the "ati" driver. Should I be using the "radeon" driver instead?

Please find xorg.conf attached.

Thanks in advance.

---

### Post by Kubunteando on 2007-06-10
At least you have to load the module DRI.

So in the section:

Section "Module"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "type1"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "v4l"
EndSection

You have to add: load "dri"

I am using the open source drivers with an ATI Radeon 9000.
I have attached my working xorg.conf with DRI running fine.

The drivers "ati" and "radeon" are the same, they will load the ATI radeon kernel module.

If the system hungs remove the "Fastwrites". In my case it hung with Edgy but I can enable it with Feisty and I get a smal improvement.

Also install the "driconf" application from the repositories and enable then HyperZ option.
You will get a boost in the performance.

---

### Post by blue_shift on 2007-06-10
Thanks, DRI is working nicely after a little fiddling and the driconf tip greatly appreciated.

---

### Post by Kubunteando on 2007-06-11
If you like playing games, you can think about installing the Open Source drivers MESA 6.5.3.
If you are using Feisty it uses version 6.5.2. But that is not enough to play some games, like Regnum Online which has a native client for Linux. With version 6.5.3 you can play it nicely.

Check: [www.mesa3d.org](www.mesa3d.org)
Also there are post in the Regnum Online forums, in Spanish though

---

### Post by blue_shift on 2007-06-11
I think the "radeon" drivier will give me full acceleration without MESA use.

---

### Post by Kubunteando on 2007-06-12
Well, the Open Source driver is actually the MESA driver.
Try:

glxinfo | grep -i opengl

This is what I get:
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.3

And I am having Direct Rendering working.
The radeon driver gives you the HW acceleration, but MESA gives you the OpenGL libraries so you can play games.

Just pointing out that there is a new MESA 6.5.3 out there and is working better than the 6.5.2, it supports more games.
Yesterday I was testing the demo of Doom 3 and it works fine even in my "old" ATI with just 32MB and the MESA drivers!

---

