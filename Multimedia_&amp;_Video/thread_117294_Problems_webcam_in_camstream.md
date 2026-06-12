---
title: "Problems webcam in camstream"
date: 2006-01-14
forum: Multimedia &amp; Video
---

### Post by gosh on 2006-01-14
I try to get my Creative WebCam Go to work on Ubuntu.
When I plug it in the USB port, this is what I get in dmesg:

< [4299684.432000] w9968cf: V4L driver for W996[87]CF JPEG USB Dual Mode Camera Chip 1:1.33-basic
< [4299684.460000] ovcamchip: v2.27 for Linux 2.6 : OV camera chip I2C driver
< [4299684.488000] usb 2-2: W996[87]CF JPEG USB Dual Mode Camera detected
< [4299684.491000] usb 2-2: V4L device registered as /dev/video1
< [4299685.820000] ovcamchip: Camera chip is an OV7610
< [4299691.320000] usb 2-2: OV7610 image sensor initialized
< [4299691.323000] usbcore: registered new driver w9968cf

So, it seems that it is recognised and the appropriate driver loaded.
But when I start camstream, I get this error:
The device experienced an error -14 (bad adress)

anyone?

---

### Post by gosh on 2006-01-31
Well, I installed it on my other desktop and again the driver seems properly installed.
The light on the webcam goes on as well. So far so good.

But I still can't get a picture.
I don't get an error message but just a black screen in Camoram or a green one in xawtv with some "noise" in the top of the screen.

anyone?

---

### Post by colgate on 2007-02-02
hi, i've got the same old webcam and the only thing I could get is a b/n image replicated 3 times in gqcam. not usefull at all.

if you manage to get it working post here how!

bye

Federico

---

