---
title: "Logitech Quickcam Orbit"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by DivineOmega on 2007-02-11
I have a Logitech Quickcam Orbit and it is becoming the only reason I need to boot into Windows. Anybody had any success in getting this to work?

I've tried 'lusb' and it simply informs me that a Logitech device is attached. It identifies the manufacturer but nothing else.

Thanks.

---

### Post by wersdaluv on 2007-03-15
Me too...

I found a driver called OrbitView, but I can't install it.

---

### Post by heather on 2007-03-29
> **wersdaluv said:**
> Me too...

I found a driver called OrbitView, but I can't install it.


HI

Has anyone gotten the Logitech Quickcam Orbit to work?

i have a Logitech Orbitron MP and can not get it to work
but my Logitech 4000 works fine..

If someone can help me i would appreciate it

Thank You

---

### Post by godfree2 on 2007-04-28
I think 2.6.20 broke support for logitech webcams,
mine wont work, no /dev/video
lsusb locksup

see
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/77456](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/77456)

I think they mean to use
modprobe uvcvideo
now in 7.04
[http://www.mail-archive.com/linux-uvc-devel@lists.berlios.de/msg00738.html](http://www.mail-archive.com/linux-uvc-devel@lists.berlios.de/msg00738.html)
but wen I try 
sudo modprobe uvcvideo
must command locks up

some dev-group killed this logitech support for some reason,
they will blame the users.
Seen no documentation warning logitech webcm users about upgrading will break webcam support. Typical, break support that itsn't broken.


good news
ubuntu 6.10 with kernel 2.6.17 still works

---

### Post by heather on 2007-04-28
Hi

Gee thats too bad
i wonder why that is


Thanks for Your reply:confused:

---

