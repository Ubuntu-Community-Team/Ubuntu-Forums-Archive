---
title: "gstreamer receiving fme stream from red5"
date: 2011-11-15
forum: Multimedia Software
---

### Post by gordonaustin on 2011-11-15
I am trying to get gstreamer to receive a stream from a red5 server, when I use the command ```
gst-launch -v rtmpsrc location=rtmp://MYIP/oflaDemo/STREAMNAME
``` when I Run this, I receive the output: ```

Setting pipeline to PAUSED ...
Pipeline is PREROLLED ...
Setting pipeline to PLAYING ...
New clock: GstSystemClock
ERROR: Closing connection: NetStream.Play.StreamNotFound

```I would like to use this as an input to webcam studio, does anybody see a problem, the stream works fine when using a flash interface such as flowplayer or a red5 demo application.

---

