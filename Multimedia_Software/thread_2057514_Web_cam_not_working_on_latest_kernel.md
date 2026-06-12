---
title: "Web cam not working on latest kernel"
date: 2012-09-13
forum: Multimedia Software
---

### Post by N00b-un-2 on 2012-09-13
I just built kernel 3.6.0-rc5 the other day and I'm very happy with its performance, particularly in terms of the open source Radeon drivers.  it would be a shame to have to roll back, but on this kernel I lose my webcam functionality.  It is a Suyin "Crystal Eye" cam which from what I've been able to gather have spotty support on Linux.
When booted with kernel 3.6.0-rc5 if I open skype or cheese, no web cam is detected.  If I boot up with the latest kernel from the repos (3.2.0-30) the camera works just fine.

Any idea how I can re-enable the camera in the bleeding edge kernel?

---

### Post by kingtiger01 on 2012-09-14
> **N00b-un-2 said:**
> I just built kernel 3.6.0-rc5 the other day and I'm very happy with its performance, particularly in terms of the open source Radeon drivers.  it would be a shame to have to roll back, but on this kernel I lose my webcam functionality.  It is a Suyin "Crystal Eye" cam which from what I've been able to gather have spotty support on Linux.
When booted with kernel 3.6.0-rc5 if I open skype or cheese, no web cam is detected.  If I boot up with the latest kernel from the repos (3.2.0-30) the camera works just fine.

Any idea how I can re-enable the camera in the bleeding edge kernel?

its probably a GSPCA based driver, there not being built with the kernel. it may be upstream([http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html))

I have a few old webcams that use it, ive been complaining about the same thing...

---

