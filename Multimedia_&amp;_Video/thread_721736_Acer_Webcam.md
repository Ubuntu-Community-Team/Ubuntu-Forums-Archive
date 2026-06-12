---
title: "Acer Webcam"
date: 2008-03-11
forum: Multimedia &amp; Video
---

### Post by jlr4u on 2008-03-11
I am trying to get the web cam to work on an Acer 5630 laptop with Camorama and Wengo.  So far, I have been able to get the Webcam to work on both Ekiga and Luvcview, but am uncertain on what to do to get Camorama and Wengo up and running.

Camorama gives the common error many others have posted: Could not connect to video device (/dev/video0) Please check connection.

I'm running kubuntu 2.6.22-14-generic
```
lsusb
Bus 005 Device 003: ID 046d:09b0 Logitech, Inc
```.

```
sudo lsmod | grep video

video                  18060  0
uvcvideo               48644  0
compat_ioctl32          2304  1 uvcvideo
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev
usbcore     
```

Any suggestions?

---

### Post by linuxwizard on 2008-03-11
I don't know anything on Wengo. Camorama does not support v4l2, Ubuntu forums are full of users asking what the "could not connect to video device (dev/video0)" error message means when they try to use Camorama. One reason is they're using a driver that requires v4l2, or they don't have v4l installed.

---

### Post by jlr4u on 2008-03-11
I have installed Skype new (Beta) version which supports a web cam, but I have the same problem.    Very discouraging.:(

---

### Post by linuxwizard on 2008-03-11
I don't use Skype, so I don't know anything on setup or configuration of it. Look over this > [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) > there are some notes at bottom of page. I only use Ekiga, Kopete & Camorama.

---

