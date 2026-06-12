---
title: "Totem won't play motion jpeg (mjpg) streams?"
date: 2009-04-28
forum: Multimedia Software
---

### Post by sgarman on 2009-04-28
I can't seem to get the totem video player to play a network mjpeg stream from an IP camera. I've had no luck with the totem that comes with Hardy or Jaunty. 

In both cases I have totem-gstreamer installed, and interestingly enough I can play the streams using the gstreamer tool gst-launch, like so:

```
gst-launch-0.10 gnomevfssrc location=http://192.168.1.253/nphMotionjpeg?Resolution=320x240 ! jpegdec! videoscale ! ffmpegcolorspace ! autovideosink
```

Someone on the gstreamer mailing list suggested that totem could be parsing the start of the http stream and getting confused about whether it's a real video stream. Is there a way to force totem to bypass this check?

Does anyone have any other suggestions? I need totem to play this stream so that I can eventually embed it in a web browser using the totem plugin. The mplayer and vlc plugins have posed performance and odd latency problems on the platform I'm trying to display these cameras on.

Thanks,

Scott

---

