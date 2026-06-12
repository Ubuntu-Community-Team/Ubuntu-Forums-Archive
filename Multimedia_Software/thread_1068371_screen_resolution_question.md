---
title: "screen resolution question"
date: 2009-02-12
forum: Multimedia Software
---

### Post by systemshock869 on 2009-02-12
I just installed xubuntu on my toshiba M45-s269 laptop.  The default resolution should be 1280x800, but under display settings there are no resolutions available.. only default.  My screen doesn't look particularly stretched, but I would like to be able to know that it is definitely set at the right resolution, or be able to change it.

I tried editing the xorg.conf file, changing the vesa driver to trident, and adding a subsection under the 'screens' section, as described in a thread i found while googling the problem.  Nothing has fixed it so I restored xorg.conf to original.

Also, 3d graphics work, like the screen savers, but they go really really slow. I guess this is a whole other problem entirely..

I just want to get everything working right!

---

### Post by ohgodnotanother1 on 2009-02-13
I too have Xubuntu and it shows "default" at the top which is the best resolution offered by the system for me.

From the documentation of the XFCE settings manager:
> Please note that the display plugin only works with XFree86 >= 4.3.0 or Xorg >= 6.7.0. In either case the XFree86-VidModeExtension  must be enabled in the Xserver to change the gamma correction and the RANDR must be enable to change the resolution and refresh rate. Check the output of xdpyinfo to see if your Xserver supports these extensions. 

Type "xdpyinfo|grep RANDR" into a terminal window and check if you get any output on that.


On my system the manual is located at:
file:///usr/share/xfce4/doc/C/index.html

---

