---
title: "Gstream  1.3.0.1 won't work"
date: 2013-12-13
forum: Multimedia Software
---

### Post by cs-spanier on 2013-12-13
Hi guys,

I'm new to Ubuntu and got a problem with the Gstreamer. I'm currently using Ubuntu 12.04 and Gstreamer version 1.3.0.1 (from the repo) to get video stream from a frame grabber (Epiphan)

during the command:

   gst-launch v4l2src device=/dev/video1 ! Autovideosink

I got the following error

Setting pipeline to PAUSED ...
ERROR:
Pipeline doesn't want to pause.
ERROR: from element
/GstPipeline:pipeline0/GstV4l2Src:v4l2src0: Cannot identify device
'/dev/video1'.
Additional debug info:
v4l2_calls.c(493):
gst_v4l2_open (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src0:
system
error: No such file or directory
Setting pipeline to NULL ...

Freeing pipeline ..

I read that I have to change the follow line in the v4l2_calls.c file
if (errno == EINVAL || errno == ENOTTY)
to
 if(errno == EINVAL || errno == ENOTTY || errno == ENODATA)


After the a successful make the problem remains. During a test with mplayer a got a stream from the Epiphan but the GStreamer won’t work.
Thanks for any comments
best regards
 
Alex

---

### Post by Yellow Pasque on 2013-12-13
It's looking for /dev/video1 and no such device exists. Either you should change the command to use the correct /dev/video device, or you should investigate why /dev/video1 does not exist.

---

