---
title: "What good is the xorg nv driver???"
date: 2007-08-04
forum: Multimedia &amp; Video
---

### Post by Ben Branch on 2007-08-04
In theory I ought to use the non-proprietary 'nv' driver for my nvidia card (7300GS). I'd
like to. However,
[LIST=1]
[*]It can't do 3d acceleration
[*]It can't report the card/GPU temperature
[*]damned if I can get 3d to work at all (googleearth)
[/LIST]

By contrast, my experience with the nvidia-supplied binary driver has been nothing
but positive, except that it is proprietary, and that if I try to roll my own kernel I'll
have a heck of a time getting an nvidia driver to work with it.

Any words of wisdom out there regarding 'nv' or future versions of it?

---

### Post by aysiu on 2007-08-04
I think *nouveau* is supposed to be the future of open source support for 3D for Nvidia cards.
[http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/)

---

### Post by onering on 2007-08-04
> nvidia card (7300GS)
I know this is not what you were asking, just want to comment...

I also have the 7300GS running Ubuntu 7.04 64-bit.  I installed the official nVidia drivers using Envy and it works great.

---

### Post by Moezzie on 2007-08-04
i have experienced the same thing. as soon as i started using the nvidia drivers i could all of a sudden user all my cards features, even svideo out!

---

### Post by david_2001 on 2007-08-05
The nv driver is a useful fallback position in the event of a broken "official" nvidia driver installation!!

---

### Post by darksidedude on 2007-08-06
the NV driver is also good for a new install so you accually get to X, without NV you would be dropped to a CLI and we all know noobs are afraid of the CLI so the nv driver is a very good leaping off point

---

