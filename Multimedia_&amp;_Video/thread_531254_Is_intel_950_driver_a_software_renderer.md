---
title: "Is intel 950 driver a software renderer?"
date: 2007-08-21
forum: Multimedia &amp; Video
---

### Post by Roque on 2007-08-21
Hi.

Today I installed xserver-xorg-video-intel for my onboard intel 950.
Performance is poorer than what's expected (compared with a 8 year old nvidia card under Ubuntu running with the nvidia propietary drivers).
The driver id is:

Mesa DRI Intel(R) 945G 20061017 x86/MMX/SSE2 version 1.3 Mesa 6.5.2

But Mesa is the open source implementation of opengl. I think it's only capable of software rendering (emulation), which is of course way slower than working with the actual videocard's hardware. Is there any way to get (even propietary) hardware-capable drivers? Could someone with knowledge explain? Many thanks!

---

### Post by tseliot on 2007-08-21
> **Roque said:**
> Hi.

Today I installed xserver-xorg-video-intel for my onboard intel 950.
Performance is poorer than what's expected (compared with a 8 year old nvidia card under Ubuntu running with the nvidia propietary drivers).

xserver-xorg-video-intel (in Feisty) is not a stable release.

you should use this one instead:
```
xserver-xorg-video-i810
```

type:
```
sudo apt-get --purge remove xserver-xorg-video-intel
```
```
sudo apt-get install --reinstall xserver-xorg-video-i810
```

and make sure that the driver is set to "i810" in the Section device of your /etc/X11/xorg.conf

then restart the Xserver.

P.S. the Intel driver does support the OpenGL

---

### Post by tseliot on 2007-08-21
and by the way:
> Whilst Mesa 3D supports several hardware graphics accelerators, it may also be compiled as a software-only renderer.

here is the rest of the article:
[http://en.wikipedia.org/wiki/Mesa_3D](http://en.wikipedia.org/wiki/Mesa_3D)

---

### Post by Roque on 2007-08-21
Thomas,

Thanks for the tip on the i810, I just reinstalled it as you suggested. 
Indeed the driver seems to work well with opengl, except for the worse performance. I am almost certain it's working in software mode; is there any way to find out for sure? Does intel publish proprietary "hardware-mode" drivers?

---

