---
title: "Odd Display issue (TwinView)"
date: 2009-11-22
forum: Multimedia Software
---

### Post by binabik80 on 2009-11-22
I have an Ubuntu 9.04 x64 setup with an nVidia 9800 video card with the 180.44 nVidia drivers.

It all works fairly well except for one odd issue.  The main desktop on (Display 0) shows the full desktop and it is all usable.  The second Desktop (Display 1) appears fine except that the desktop seems cut off.  The background displays similar to a 4/3 aspect ratio left aligned with the space after the desktop background black.  I can move my mouse past the desktop background and into the black space, but any application I open is confined to  the smaller space where the desktop background image is.

I have the resolution set to the Native resolution and frequency for that monitor and besides this odd issue I am very happy with the configuration.

Any ideas?

---

### Post by binabik80 on 2009-11-24
Just wanted to let anyone interested that I figured out the problem.

The issue was the display resolution on the Primary Monitor (Head0) was set to a lower resolution than the secondary monitor (head1) so the desktop was restricted to the width of the lower resolution.  Once I increased the resolution on the primary monitor I had the full resolution on both monitors.

Add issue or bug?

---

