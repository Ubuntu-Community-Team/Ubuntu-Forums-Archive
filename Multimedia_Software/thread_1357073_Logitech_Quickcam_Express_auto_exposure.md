---
title: "Logitech Quickcam Express auto exposure"
date: 2009-12-16
forum: Multimedia Software
---

### Post by Tee.Gee on 2009-12-16
Hi,

I've got a Logitech QuickCam Express running on ubuntu karmic
(2.6.31-16-generic-pae). I have compiled qc-usb-source 0.6.6-6ubuntu2
with the patch from this email:
[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg685578.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg685578.html).
The camera works but the automatic exposure time (or brightness)
adjustment doesn't, so I can only see proper images with the right
amount of light, which isn't the case very often. Unfortunately, I
cannot read any settings with qcset:
qcset: ioctl VIDIOCGCHAN (Invalid argument)
Any ideas how to fix this?

Cheers
Tom

---

### Post by ianb1469 on 2010-01-10
Most software doesn't seem to work with that camera, however v4l2ucp does.

You can get it from: [http://sourceforge.net/projects/v4l2ucp/](http://sourceforge.net/projects/v4l2ucp/)

i.

---

### Post by Tee.Gee on 2010-01-18
The software worked fine with hardy. Upgrading to jaunty killed it, karmic didn't fix it.
I think, I might go back to hardy - sadly!

---

### Post by lyall on 2010-01-20
see the following link 
[https://help.ubuntu.com/community/Webcam]("https://help.ubuntu.com/community/Webcam")

at the bottom there  is section for **Setting brightness, contrast, color etc. on some webcams**

hope this works for you

good luck and have fun learning

---

