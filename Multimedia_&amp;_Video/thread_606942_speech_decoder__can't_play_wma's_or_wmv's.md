---
title: "speech decoder?  can't play wma's or wmv's"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by weareallkosh on 2007-11-08
Hi, I've read several other threads on this and they don't match my issue.
Myself and a co-worker/friend recently made the switch to Ubuntu for our work computers.  wmv/wma support worked pretty much out of the box with his laptop but it's broken on mine.

I have gstreamer installed, and have the codecs as you can see
gst-inspect-0.10 |grep wm
ffmpeg:  ffdec_wmav2: FFMPEG Windows Media Audio v8/9 decoder
ffmpeg:  ffdec_wmav1: FFMPEG Windows Media Audio v7 decoder
ffmpeg:  ffdec_wmv3: FFMPEG Windows Media Video v9 decoder
ffmpeg:  ffdec_wmv2: FFMPEG Windows Media Video v8 decoder
ffmpeg:  ffdec_wmv1: FFMPEG Windows Media Video v7 decoder
ffmpeg:  ffenc_wmv2: FFMPEG Windows Media Video v8 encoder
ffmpeg:  ffenc_wmv1: FFMPEG Windows Media Video v7 encoder
typefindfunctions: video/x-ms-asf: asf, wm, wma, wmv

If I try to play a wma in vlc I get no sound... but the progress bar plays.
If I try to play it in totem I get the error that playback of this file requires a " windows media player speech decoder plugin" which is not installed.  I couldn't find anything linux specific on google trying search terms out of that error.

The file is not DRM protected, plays fine on another linux box, both using the same ubuntu install from the same cd.

Thanks in advance....

---

### Post by ae7@live on 2008-05-31
I have the same problem in playing the followin link in totem 
mms://streamwebtown.com/nogoomfmblog
any one can help me?

---

