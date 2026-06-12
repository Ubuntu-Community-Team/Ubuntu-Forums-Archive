---
title: "ETA for Sandy Bridge video driver?"
date: 2011-08-23
forum: Multimedia Software
---

### Post by CalSkeptic on 2011-08-23
CPU: Intel i3-2100

Video works OK in Windoze XP but just a black screen in Ubuntu 11.04.  Any idea when somebody will come up with a working driver?

---

### Post by realzippy on 2011-08-23
You need a kernel >= 2.38.8...,
but normally it should boot.

---

### Post by CalSkeptic on 2011-08-23
> **realzippy said:**
> You need a kernel >= 2.38.8...,
but normally it should boot.

Yep, you are right, rz.  I took out the temporary video card and plugged back into the internal video.  The first time I booted it was a bit unstable, but the second time it seems to be working normally.  Thanks!

---

### Post by realzippy on 2011-08-23
Means,you upgraded kernel and then it worked?

---

### Post by CalSkeptic on 2011-08-23
> **realzippy said:**
> Means,you upgraded kernel and then it worked?

Oops!  No, I take it all back.  Two hard freezes later I went back to the video card, which works fine.  Perhaps I should wait for 11.10 and then try again?

Biostar H67MU3
Intel i3-2100
8Gb DDR3
SATA 6 HD
11.04, kernel 2.6.38-11
Dual-boot w/Windows XP

---

### Post by realzippy on 2011-08-23
Which version of xserver-xorg-video-intel do you have installed?
Here I3 graphics work great with 2:2.14.0 ...
Running kernel 3.0.1-030001-generic,but read somewhere that 2.6.38.8 would be enough...

---

### Post by CalSkeptic on 2011-08-23
> **realzippy said:**
> Which version of xserver-xorg-video-intel do you have installed?
Here I3 graphics work great with 2:2.14.0 ...
Running kernel 3.0.1-030001-generic,but read somewhere that 2.6.38.8 would be enough...

Mine says 2:2.16.0, but the video is still flaky.  Do you have an H67MB?  Could the problem be with that?  Hmmm... it seems rock-solid with Windoze.

---

