---
title: "ubuntu 8.10 gspcav2 webcam driver (v4l2)"
date: 2008-12-07
forum: Multimedia Software
---

### Post by bbspin on 2008-12-07
Ubuntu 8.10 switched to v4l2 driver (gspcav2), at least for my webcam. And I am writing my own webcam capture program that would use it. 

I have this web camera: 
   Bus 002 Device 003: ID 046d:08da Logitech, Inc. QuickCam Messanger

When I enumerate all posible pixel modes that this driver supports, I only get JPEG compressed mode. no RGB anymore? I know JPEG should go faster on non USB2.0 webcams, but I still wan't to use RGB 24, or BGR 24 modes! Anyone knows why driver doesn't support this anymore?

---

### Post by bbspin on 2008-12-07
I've found out, that gspcav1 received JPEG data stream from the HW, this was then uncompressed in kernel space as tasklet and send to user space... It's a shame that gspcav2 can't do that anymore :/

---

