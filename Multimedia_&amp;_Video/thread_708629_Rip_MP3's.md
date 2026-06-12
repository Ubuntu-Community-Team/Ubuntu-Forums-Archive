---
title: "Rip MP3's?"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by CarlosinFL on 2008-02-26
I am using Sound Juicer to rip MP3's and I read the guide however it appears to be dated.

What exactly do I need to install as far as Gstreamer goes?

There are a thousand options for this plugin...I just want to rip my CD's as MP3 format...

```
gstreamer-dbus-media-service - Media service for Ubuntu Mobile
gstreamer0.10-ffmpeg - FFmpeg plugin for GStreamer
gstreamer0.10-fluendo-mp3 - Fluendo mp3 decoder GStreamer plugin
gstreamer0.10-fluendo-mpegdemux - Fluendo GStreamer plugin for MPEG2 demuxing
gstreamer0.10-gl - GStreamer plugin for OpenGL output
gstreamer0.10-gnonlin - non-linear editing module for GStreamer
gstreamer0.10-gnonlin-dev - development files of the non-linear editing module for GStreamer
gstreamer0.10-pitfdll - GStreamer plugin for using MS Windows binary codecs
gstreamer0.10-plugins-bad - GStreamer plugins from the "bad" set
gstreamer0.10-plugins-bad-dbg - GStreamer plugins from the "bad" set
gstreamer0.10-plugins-bad-doc - GStreamer documentation for plugins from the "bad" set
gstreamer0.10-plugins-farsight - plugins for Gstreamer for Audio/Video conferencing
gstreamer0.10-plugins-ugly - GStreamer plugins from the "ugly" set
gstreamer0.10-plugins-ugly-dbg - GStreamer plugins from the "ugly" set
gstreamer0.10-plugins-ugly-doc - GStreamer documentation for plugins from the "ugly" set
gstreamer0.10-schroedinger - GStreamer plugin for encoding/decoding of Dirac video streams
gstreamer0.10-sdl - GStreamer plugin for SDL output
kaffeine-gstreamer - Gstreamer engine for kaffeine media player

```

Can someone please point me in the direction...

---

### Post by logos34 on 2008-02-26
I believe gstreamer0.10-plugins-ugly is what you need (although it's been awhile since I've fiddled with Soundjuicer--I use grip, abcde, k3b or eac)

[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

[https://help.ubuntu.com/community/CDRipping#head-f109ee313aa77bf2997e6499584438e9f7691d58](https://help.ubuntu.com/community/CDRipping#head-f109ee313aa77bf2997e6499584438e9f7691d58)

---

### Post by cozmicharlie on 2008-02-26
You should also look here [https://help.ubuntu.com/community/RestrictedFormats#head-e69e0c62de07b1e2b560c1ad6b68823328906067](https://help.ubuntu.com/community/RestrictedFormats#head-e69e0c62de07b1e2b560c1ad6b68823328906067)

---

### Post by wolfen69 on 2008-02-26
the fluendo or lame mp3 should be fine.

---

### Post by disturbedite on 2008-02-27
i'd recommend using a different format if you can, such as flac (lossless), or ogg (lossy, like mp3).  they are FOSS, mp3 is not.
but if you need mp3, then lame should suffice, as wolfen69 said.

---

