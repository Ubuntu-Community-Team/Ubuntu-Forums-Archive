---
title: "GStreamer element x264enc"
date: 2009-12-29
forum: Multimedia Software
---

### Post by Jompa on 2009-12-29
Hi.
I want to convert some videos to a format so that I can play them on my HTC Tattoo phone. I found Arista Transcoder, but the program needs a certain plugin to converte the files. My system doesn't find what is needed. It needs:
> GStreamer element x264enc

Can anyone help me get this?

---

### Post by VertexPusher on 2009-12-29
Install gstreamer0.10-plugins-ugly-multiverse.

---

### Post by timsdeepsky on 2009-12-29
Do you have to install x264 in your system for this??....[http://ubuntuforums.org/showthread.php?t=786095]("http://ubuntuforums.org/showthread.php?t=786095")

---

### Post by skrimpy on 2010-02-18
> **VertexPusher said:**
> Install gstreamer0.10-plugins-ugly-multiverse.

Thanks, this solved my problem right away!

---

### Post by andynine on 2010-03-08
This worked for me after spending the last three days trying
thanks :)

---

### Post by drsouvikkumar on 2010-03-23
> **VertexPusher said:**
> Install gstreamer0.10-plugins-ugly-multiverse.

Thanks !
anyway is there any better MP4 converter than arista ?

---

### Post by ellannjohnson on 2010-06-06
Thanks. Worked for me too on Lynx.

---

### Post by skyttan on 2011-04-24
> **VertexPusher said:**
> Install gstreamer0.10-plugins-ugly-multiverse.

Thank you! I am using Natty and this worked for me! :D

---

### Post by virgoptrex on 2011-08-26
Why not use ffenc_mpeg4 instead?
e.g. 
```

gst-launch -v rtspsrc location="rtsp://<user>:<pass>@<ip>/mpeg4/1/media.amp" ! rtpmp4vdepay! ffdec_mpeg4 ! videoscale ! 'video/x-raw-yuv, width=640, height=480'! videorate ! 'video/x-raw-yuv,framerate=30/1' ! ffmpegcolorspace ! 'video/x-raw-yuv,format=(fourcc)I420' ! ffenc_mpeg4 ! avimux! queue! filesink location=test.avi

```

---

