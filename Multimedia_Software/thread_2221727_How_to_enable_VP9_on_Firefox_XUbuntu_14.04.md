---
title: "How to enable VP9 on Firefox XUbuntu 14.04"
date: 2014-05-03
forum: Multimedia Software
---

### Post by Bjorg on 2014-05-03
I am on XUbuntu 14.04 AMD64. (Well actually I have installed the system with that approx 300MB CD image that allows you to install anything, Ubuntu, Xubuntu, Kubuntu, Ubuntu Studio etc..., I installed Xubuntu and Ubuntu Studio, and when the system boots the Ubuntu Studio welcome screen appears, and then I am taken to the XFCE destop ) 

Chromium already lists everything enabled when visiting [https://www.youtube.com/html5](https://www.youtube.com/html5)

But for Firefox 29, visiting that same page shows that [H.264], [Media Source Extensions], [MSE & H.264], and [MSE & WebM VP9] are all disabled.

I read some time ago that Firefox 28 already was shipping with the VP9 codec. Why are these not enabled? How to enable them?

Youtube videos are actually played with HTML5, not Flash, but only with very low resolution (240p or 360p). (Full resolution with HTML5 on Chromium of course)

Thanks

Alex

---

### Post by monkeybrain20122 on 2014-05-03
h264 decoding is not working in FF in Ubuntu 14.04 because Canonical removed the package gstreamer0.10-ffmpeg and FF doesn't support gstreamer1.0 (it will be supported in FF30, I heard) In the mean time you need to install gstreamer0.10-ffmpeg form this ppa.

[https://bugs.launchpad.net/~mc3man/+archive/trusty-media](https://bugs.launchpad.net/~mc3man/+archive/trusty-media)

---

### Post by Yellow Pasque on 2014-05-03
The problem is that FF 29 and earlier still used gstreamer0.10 and the gstreamer0.10-ffmpeg package is no longer available.

It looks like the Firefox team is working on enabling gstreamer1.0: [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa/+packages](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa/+packages)

That will allow h264 and probably vp9: [http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-plugin-vpx.html](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-plugin-vpx.html)

---

### Post by Bjorg on 2014-05-03
Thanks for the reply to you both.

---

