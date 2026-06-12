---
title: "UVC Video - logitech sphere"
date: 2008-03-24
forum: Multimedia &amp; Video
---

### Post by Jellman on 2008-03-24
Hi there, ive got a problem getting my logitech sphere to work under ubuntu (7.10 & 8.04 beta).

The problem is as follows: 

I can get the webcam to work, i download the UVC svn trunk and compile it. 

```

sudo bash
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
cd trunk
make
make install
modprobe uvcvideo

```

The problem is when i reboot, and load up a webcam app, for example cheese. The webcam is not working. To get it to work again i need to unload the modual and then reload it, which is a ball ache!

Any ideas on how to get it just to work?

Scott

---

