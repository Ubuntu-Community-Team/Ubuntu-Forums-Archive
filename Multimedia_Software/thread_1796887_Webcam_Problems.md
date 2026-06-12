---
title: "Webcam Problems"
date: 2011-07-04
forum: Multimedia Software
---

### Post by AEL21 on 2011-07-04
I have a webcam that periodically gets dumped and I have to unplug and plug back in to get it to work again. I think it has to do with somethign about how the webcam is USB 2.0 but my PC is USB 1.0, even though it says it is USB 2.0. In Windows it would also dump it but then it would automatically remount it. Is there a way to do this in Ubuntu?

I'm using Ubuntu 11.04.

---

### Post by no2498 on 2011-07-04
on some older computers the front was usb 1.0 and the back was usb 2.0

if you have gstreamer installed you may try setting the plugin to auto find your cam

in a terminal type gstreamer-properties click enter

click video
set the plugin to auto find your cam

you can test the cam with the bottom test button

---

