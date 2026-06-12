---
title: "gstreamer0.10-ffmpeg useless?"
date: 2010-10-05
forum: Multimedia Software
---

### Post by teresaejunior on 2010-10-05
Hello!

I know we have to install gstreamer0.10-plugins-*, but what is the use of gstreamer0.10-ffmpeg? The descriptions says:

> This GStreamer plugin supports a large number of audio and video compression formats through the use of the FFmpeg library. The plugin contains GStreamer elements for decoding 90+ formats (AVI, MPEG, OGG, Matroska, ASF, ...), demuxing 30+ formats and colorspace conversion.

But if I don't install gstreamer0.10-plugins-*, I get:

> "Warning: You do not seem to have the package gstreamer0.10-plugins-good installed.
          Some video features have been disabled." 


ffmpeg should be able by itself to decode and encode almost anything, so why is it necessary to install the other plugins?

---

### Post by mc4man on 2010-10-05
> **Some** video features have been disabled.

They provide different things, the ffmpeg plugin is mainly for codec support.
If you want to see what the ffmpeg one provides, or at least currently on your machine (if you have gst-inspect
```
gst-inspect plugin ffmpeg 
```  

While ubuntu/debian breaks up the plugins a little bit differently 

[http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/)

Somewhat silly to have removed the good plugin, your choice

---

### Post by teresaejunior on 2010-10-05
> They provide different things, the ffmpeg plugin is mainly for codec support.
If you want to see what the ffmpeg one provides, or at least currently on your machine (if you have gst-inspect
```
gst-inspect plugin ffmpeg 
```

I see, thanks! I thought it was something like the phonon-backends, which you can choose between xine, vlc, mplayer, gstreamer... So ffmpeg would be an alternative to the others.

---

