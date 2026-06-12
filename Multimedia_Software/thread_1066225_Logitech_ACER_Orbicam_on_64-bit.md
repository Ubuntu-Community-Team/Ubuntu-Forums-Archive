---
title: "Logitech ACER Orbicam on 64-bit"
date: 2009-02-10
forum: Multimedia Software
---

### Post by brazzmonkey on 2009-02-10
Hello there,
a while back I got my webcam working using the gspca driver on Ubuntu 32-bit. Lately I'm having weird issues with this webcam on a recent 64-bit installation: garbled image mostly made of green lines and garbage.

Anyone having this issue?

Device ID is :
```
$ lsusb
Bus 001 Device 003: ID 046d:0896 Logitech, Inc.

```

---

### Post by brazzmonkey on 2009-02-15
*bump*

---

### Post by monstara on 2009-04-28
I have the same issue in Jaunty, and previously in Intrepid, 32-bit system.
Now I see that xawtv opens the camera fine, but for instance in PD or Skype I get similar crap to what brazz described. Interestingly, with a different camera I get *different kind of crap* :KS
Recently I reinstalled the gspca and v4l, but no change. 

I am attaching screens from both cameras(in PD using Gem, Skype's image is a bit different but Skype preview is low-res):
.._Gem  - 046d:0896 Logitech, Inc. OrbiCam
.._Trust - 0ac8:307b Z-Star Microelectronics Corp. USB 1.1 WebCam
(and, by the way, cool glitches! would be nice to know how to reproduce them)

---

### Post by josta7 on 2009-06-24
I have the same issue too, same green lines. Only I'm in 9.04. I have tried so many different things!  If you have any advice, please point me to it! I am ](*,) about it! TYIA!

---

### Post by brazzmonkey on 2009-07-08
It looks like things got broken since gspca has been included in the kernel.
I no longer use Ubuntu on my computer, but I can tell you I'm still having this issue with the latest kernel. 

It looks like there's something wrong with vc032x module...

---

### Post by brazzmonkey on 2009-07-24
Nevermind, it works again using kernel 2.6.30.2...

---

