---
title: "No video in Totem playing internet stream"
date: 2010-01-22
forum: Multimedia Software
---

### Post by drhabber on 2010-01-22
I have a strange issue with Totem (Ubuntu 9.10 fully up to date) - when playing rtsp:// stream it won't show video. 

The stream codecs are WMA8 for audio and WWV9 for video. Everything seems to be installed and set up properly but somehow Totem (or gstreamer ?) is not using gstreamer-ffmpeg or something like that. However when I'm trying to play the stream from a clean install of Ubuntu 9.10 in Virtualbox, then a window pops up in Totem telling me that gstreamer-ffmpeg has to be downloaded for WMA8 audio and WMV9 video - then everything plays smooth. 

Removing the gstreamer-ffmpeg on my native install and installing it the Totem way results with the same message except it wants to download gstreamer-ffmpeg only for WMA8 audio (!).

Any ideas ?

---

