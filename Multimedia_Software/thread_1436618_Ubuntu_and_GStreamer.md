---
title: "Ubuntu and GStreamer"
date: 2010-03-22
forum: Multimedia Software
---

### Post by gentlemich on 2010-03-22
Hello,
I am trying to stream a video between two Ubuntu 9.04 stations using GStreamer.

The following code is run on the emitting machine:
```
gst-launch videotestsrc ! queue ! ffenc_mjpeg ! udpsink port=5000 host=192.168.1.100 -v
```And the following on the receiving machine with IP 192.168.1.100:
```
gst-launch udpsrc port=5000 caps="image/jpeg, width=320, height=240, framerate=30/1" ! queue ! ffdec_mjpeg ! ximagesink sync=true -v
```Whatever the order I'm running them (emit first or receive first), I'm getting the following error once both are connected (I can see the Ethernet lights blinking):

ERROR*: element /GstPipeline:pipeline0/GstUDPSrc:udpsrc0*: internal error data flow.
gstbasesrc.c(2458): gst_base_src_loop (): /GstPipeline:pipeline/GstUDPSrc:udpsrc0:
**streaming task paused, reason not-negotiated (-4)**
Execution ended after 3191625000 ns.
PAUSED...

What's happening? I have set the caps and it still shows me the error.

Thanks,
Mike

[Find local services on Skilto]("http://www.skilto.com")

---

