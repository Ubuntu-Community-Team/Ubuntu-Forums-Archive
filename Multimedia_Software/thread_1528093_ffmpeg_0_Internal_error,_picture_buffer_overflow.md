---
title: "ffmpeg :0:: Internal error, picture buffer overflow"
date: 2010-07-10
forum: Multimedia Software
---

### Post by sviperll on 2010-07-10
I have the following error during playback of h264 movies with totem:

```
$ totem movie.mkv --gst-debug-level=2
```gives

```

...
0:00:49.204258363  6306      0x37b7150 ERROR                 ffmpeg :0:: Internal error, picture buffer overflow

```However mplayer plays this file without problems, ignoring the fact that it uses the same library (libavcodec52)

I have the basic Ubuntu 10.04 installation with the following packages:
```

gstreamer0.10-ffmpeg 0.10.10-1
mplayer 2:1.0~rc3+svn20090426-1ubuntu16

```

---

