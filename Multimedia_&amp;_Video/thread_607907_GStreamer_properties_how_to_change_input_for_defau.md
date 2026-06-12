---
title: "GStreamer properties: how to change input for default video device?"
date: 2007-11-09
forum: Multimedia &amp; Video
---

### Post by 0x656b694d on 2007-11-09
Hi,

How do i change the input source for the default video device in gstreamer properties?
I've got a TV tuner and want to set its s-video input as the default. Now i have the following settings:
```
v4l2src device="/dev/video0"
```
But it shows TV in Skype, for instance.
How do i set input=1 for this device? I mean the following command launches mplayer with the picture from the correct input:
```
mplayer tv:// -tv driver=v4l2:input=1:amode=0:width=384:height=288:outfmt=yv12:device=/dev/video0...
```

Thanks!
-Mike

---

