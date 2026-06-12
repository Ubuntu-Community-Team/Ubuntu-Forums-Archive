---
title: "Another webcam not working"
date: 2012-03-18
forum: Multimedia Software
---

### Post by Deeday on 2012-03-18
This is the only way I can get my webcam to at least turn on:

1) From gstreamer-properties, Video, Default input, I change the plugin to Custom and Pipeline to ```
v4l2src device="/dev/video0"
``` Pressing the Test button gives ```
Error running pipeline 'Custom': Error starting streaming on device '/dev/video0'. [gstv4l2object.c(2143): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1: system error: No such device]

```

2) I change the device to video1 and I get ```
Error running pipeline 'Custom': Error starting streaming on device '/dev/video1'. [gstv4l2object.c(2143): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src2: system error: No such device]

```

3) I change back to video0 and _it works_, i.e. I get the test picture from my webcam.

The behaviour is repeatable, although sometimes it takes one additional step, so it ends up working with video1, instead of video0.

Needless to say, Skype cannot get the webcam to work (blank screen) and it's been like that for ages (over a year, I believe) but now I really would like to sort it out.

Thanks for any advice! ):P

My system:
Logitech Orbicam built-in on Acer Aspire 5630 laptop
Ubuntu Oneiric 64
Kernel 3.0.0.17

---

### Post by Deeday on 2012-03-21
Anyone got any ideas on this one?

Cheers.

---

### Post by Deeday on 2012-03-31
So I guess this problem is hopeless :frown:

---

### Post by Deeday on 2013-02-16
In the end I think it was a hardware problem.

The built-in camera is fitted so that it can swivel up-and-down (all the way to facing the opposite way to the user) and I suspect there was some  dodgy contact, as on many occasions jiggling the camera a little bit brought it online, at the next attempt of the described procedure.

---

