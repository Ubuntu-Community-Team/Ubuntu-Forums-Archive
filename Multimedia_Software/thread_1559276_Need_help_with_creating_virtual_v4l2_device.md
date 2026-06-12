---
title: "Need help with creating virtual v4l2 device"
date: 2010-08-23
forum: Multimedia Software
---

### Post by oilgame on 2010-08-23
Hey.

I'm trying trying to use computer x's webcamera on computer y.

I can view computer x's webcamera on computer y by running these commands:
```
x$ gst-launch v4l2src device=/dev/video0 ! videoscale! video/x-raw-yuv,width=320,height=240 ! ffmpegcolorspace ! jpegenc ! multipartmux ! tcpserversink host=10.0.0.240 port=5000
y$ gst-launch tcpclientsrc host=10.0.0.240 port=5000 ! multipartdemux ! jpegdec ! autovideosink
```

I tryed this to create virtual v4l2 to computer y from it:
```
x$ gst-launch v4l2src device=/dev/video0 ! videoscale! video/x-raw-yuv,width=320,height=240 ! ffmpegcolorspace ! jpegenc ! multipartmux ! tcpserversink host=10.0.0.240 port=5000
y$ gst-launch tcpclientsrc host=10.0.0.240 port=5000 ! multipartdemux ! jpegdec ! v4l2sink device=/dev/video0
```
But it fails like this:
```
Setting pipeline to PAUSED ...
ERROR: Pipeline doesn't want to pause.
ERROR: from element /GstPipeline:pipeline0/GstV4l2Sink:v4l2sink0: Cannot identify device '/dev/video0'.
Additional debug info:
v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline0/GstV4l2Sink:v4l2sink0:
system error: No such file or directory
Setting pipeline to NULL ...
Freeing pipeline ...
```

Should I first create blank v4l2-device for it and how?

Thanks.

---

### Post by oilgame on 2010-08-26
Anybody?

---

