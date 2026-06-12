---
title: "Gstreamer shoutcast video streaming hang up with socket error after a while"
date: 2009-02-27
forum: Multimedia Software
---

### Post by velmont on 2009-02-27
Hi,
I'm using the truly excellent [GStreamer script Video4Linux2]("http://giss.tv/wiki/index.php/Streaming_Tools#GStreamer_2") from giss.tv. I used both the firewire (with DV-camera) and webcam version at work yesterday.

I'm streaming to my icecast2-server with a whole lot of bandwidth (so that many others can watch the video/conference). I've got even faster broadband here at home than at work, but still I get problems here.

When I connect and start streaming video, it works for about 2-3 minutes, before I get the following error:

```
Error: Could not write to resource. gstshout2.c(618): gst_shout2send_render (): /GstPipeline:pipeline5/GstShout2send:shout2send2:
shout_send() failed: Socket error

```

As you can see, I suddenly get a socket error. Does anyone have an idea about what it can be? I'd like to try from a few other connections as well, but it have to work from everywhere because I don't know which places we'll broadcast from in the future.

The GST-function is here:

```
gstreamer command :  v4l2src device=/dev/video0 ! video/x-raw-yuv,width=320,height=240 ! queue ! videorate ! video/x-raw-yuv,framerate=25/2 ! videoscale ! video/x-raw-yuv,width=360,height=288 ! ffmpegcolorspace ! tee name=tscreen ! queue ! autovideosink tscreen. ! queue ! theoraenc quality=20 ! queue ! oggmux name=mux osssrc device=/dev/dsp ! audio/x-raw-int,rate=22050,channels=1 ! queue ! audioconvert ! vorbisenc quality=0.2 ! queue ! mux. mux. ! queue ! shout2send ip=example.com port=8002 mount=test.ogg password=test streamname="Test test" description="Test" genre= url=http://example.com
```

I could try it alone with gst-launch.

Actually I can't, I get this error:

```
Setting pipeline to PAUSED ...
Pipeline is live and does not need PREROLL ...
Setting pipeline to PLAYING ...
New clock: GstSystemClock
ERROR: from element /GstPipeline:pipeline0/GstV4l2Src:v4l2src0: Internal data flow error.
Additional debug info:
gstbasesrc.c(2234): gst_base_src_loop (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src0:
streaming task paused, reason not-linked (-1)
Execution ended after 260248219 ns.
Setting pipeline to PAUSED ...
Setting pipeline to READY ...
Setting pipeline to NULL ...
FREEING pipeline ...
```

Help...? :-)

---

### Post by velmont on 2009-02-27
Ok. This was obviously the wrong forum. It's probably more networking-related. But I can't move it.

Anyways, I put down the quality from 27 to 20, but bumped up the resolution to 640x480. I guess maybe my computer couldn't keep up. Or maybe there was some traffic congestion, which should be strange since I've got 10mbit internet.

Well, -- it has been working for a while now. I don't like that I didn't really find a real culprit though.

---

