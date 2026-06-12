---
title: "suddenly low resolution and cannot increase"
date: 2012-08-31
forum: Multimedia Software
---

### Post by evencoil on 2012-08-31
I have two identical monitors connected to a Radeon HD6450, one through a DVI output and one through a DPI-DVI output. They used to both run in 1600x1200 resolution.

The other day I boot up my Kubuntu 11.10 installation and for no apparent reason one of the screens is at 1024 x 768. When I look at monitor settings 1600x1200 is not an option.

I have done some checks by switching up monitors and cables. They are fine--the problem is that whichever is connected to the DPI-DVI output shows up in the lower resolution with no option to change to the higher resolution.

Any idea what the problem is? Is this an Xorg issue? If so, can I reset it somehow? Perhaps my video card went bad in the DPI port? Thanks

---

### Post by ectechnologies on 2012-08-31
Hi,

I had the problem with a client.

On the taskbar where you turn of your computer, click the drop down menu and click on displays.

---

### Post by evencoil on 2012-08-31
That's the dialog I have been trying to use, but there is no longer the option to choose 1600x1200 resolution.

---

### Post by ectechnologies on 2012-08-31
If you have done any updates lately then 1600x1200 is no longer in the available list of resolutions.

But just to try us this code:

Press Ctrl-Alt-T

xrandr -s 1600x1200

---

