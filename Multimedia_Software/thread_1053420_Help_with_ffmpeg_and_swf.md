---
title: "Help with ffmpeg and swf"
date: 2009-01-28
forum: Multimedia Software
---

### Post by pcasanov on 2009-01-28
how can i add swf playback for ffmpeg?  I think that libavcodec/libavformat unstripped supports this, but how do I tell ffmpeg to enable these libraries?

I know that there are other products that do this, but need to do it with ffmpeg.

---

### Post by pcasanov on 2009-01-28
Tried to compile ffmpeg with svn trunk and svn build 15261 as said in Ubuntu Tutorial, but all builds end up with make failing "make: *** [libswscale/swscale.o] Error 1".

Please help:(

---

### Post by FakeOutdoorsman on 2009-01-30
> **pcasanov said:**
> how can i add swf playback for ffmpeg?  I think that libavcodec/libavformat unstripped supports this, but how do I tell ffmpeg to enable these libraries?

I know that there are other products that do this, but need to do it with ffmpeg.
If you're using Intrepid (8.10) you can install the **libavcodec-unstripped-51** package to enable restricted encoders / decoders.  FFmpeg will automatically use this package once it is installed.  However, I don't think you need this package to decode SWF that contain a flv video stream.  I'm not sure if compressed SWF is even supported.
> **pcasanov said:**
> Tried to compile ffmpeg with svn trunk and svn build 15261 as said in Ubuntu Tutorial, but all builds end up with make failing "make: *** [libswscale/swscale.o] Error 1".

Please help:(
Did you get this error by following this tutorial?
[HOWTO: Compile the latest ffmpeg and x264 from source](http://ubuntuforums.org/showthread.php?t=786095)

---

