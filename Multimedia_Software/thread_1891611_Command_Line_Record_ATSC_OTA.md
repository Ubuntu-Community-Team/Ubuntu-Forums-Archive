---
title: "Command Line Record ATSC OTA"
date: 2011-12-06
forum: Multimedia Software
---

### Post by greenpin on 2011-12-06
I have a CLI only Ubuntu Server, and would like to record some ATSC OTA shows with an HDHomeRun or other tuner. Every PVR application I have found so far requires X windows. I only want to record on the server and will playback on a digital video player connected to my TV. Is anyone aware of a CLI recording application like this?

---

### Post by lukeiamyourfather on 2011-12-06
If the device is supported by GStreamer then use that (gst-launch). The below example is from a webcam tutorial but you get the idea.

```

gst-launch v4l2src ! 'video/x-raw-yuv,width=640,height=480,framerate=30/1' ! \
tee name=t_vid ! queue ! xvimagesink sync=false t_vid. ! queue ! videorate ! \
video/x-raw-yuv,framerate=30/1 ! theoraenc ! queue ! mux. \
alsasrc device=hw:1,0 ! audio/x-raw-int,rate=48000,channels=2,depth=16 ! \
queue ! audioconvert ! queue ! vorbisenc ! queue ! mux. \
oggmux name=mux ! filesink location=me_funny_dancing.ogg

```

Here's the link to where that command is from.

[http://www.twm-kd.com/linux/webcam-and-linux-gstreamer-tutorial/](http://www.twm-kd.com/linux/webcam-and-linux-gstreamer-tutorial/)

---

