---
title: "GnomeBaker error burning audio CD's"
date: 2006-11-27
forum: Multimedia &amp; Video
---

### Post by KompresZor on 2006-11-27
When trying to make audio cd's with GnomeBaker I get the following error - *"GStreamer encountered a general resource error".*
When using Serpentine I get this error message - *"If you're having problems opening certain files make sure you have the GStreamer plugins needed to decode them".*

I have no problem playing mp3 files the only time I get an error is when I try to create an Audio CD. From the errors above I going to assume it's a problem with a Gstreamer pluging. This ia a list of the GStreamer plug-in's ect. I have installed. But I have no idea which ones might be in conflict, any help would be appreciated!

```
gstreamer0.10-alsa - GStreamer plugin for ALSA
gstreamer0.10-esd - GStreamer plugin for ESD
gstreamer0.10-ffmpeg - FFmpeg plugin for GStreamer
gstreamer0.10-fluendo-mp3 - Fluendo mp3 decoder GStreamer plugin
gstreamer0.10-fluendo-mpegdemux - Fluendo GStreamer plugin for MPEG2 demuxing
gstreamer0.10-gl - GStreamer plugin for OpenGL output
gstreamer0.10-gnomevfs - GStreamer plugin for GnomeVFS
gstreamer0.10-gnonlin - non-linear editing module for GStreamer
gstreamer0.10-pitfdll - GStreamer plugin for using MS Windows binary codecs
gstreamer0.10-plugins-bad - GStreamer plugins from the "bad" set
gstreamer0.10-plugins-bad-multiverse - GStreamer plugins from the "bad" set (Multiverse Variant)
gstreamer0.10-plugins-base - GStreamer plugins from the "base" set
gstreamer0.10-plugins-base-apps - GStreamer helper programs from the "base" set
gstreamer0.10-plugins-good - GStreamer plugins from the "good" set
gstreamer0.10-plugins-ugly - GStreamer plugins from the "ugly" set
gstreamer0.10-plugins-ugly-multiverse - GStreamer plugins from the "ugly" set (Multiverse Variant)
gstreamer0.10-sdl - GStreamer plugin for SDL output
gstreamer0.10-tools - Tools for use with GStreamer
gstreamer0.10-x - GStreamer plugins for X11 and Pango
```

---

### Post by mcduck on 2006-11-27
> **KompresZor said:**
> When trying to make audio cd's with GnomeBaker I get the following error - *"GStreamer encountered a general resource error".*
When using Serpentine I get this error message - *"If you're having problems opening certain files make sure you have the GStreamer plugins needed to decode them".*

I have no problem playing mp3 files the only time I get an error is when I try to create an Audio CD. From the errors above I going to assume it's a problem with a Gstreamer pluging. This ia a list of the GStreamer plug-in's ect. I have installed. But I have no idea which ones might be in conflict, any help would be appreciated!


I'm not sure, but I remember GnomeBaker in Dapper using gstreamer 0.8 instead of 0.10 like other apps do. You could try installing gstreamer0.8-plugins..

---

### Post by KompresZor on 2006-11-27
I had thought about that but the version of GnomeBker installed is 0.6.0-0ubuntu2 and the recomended plugins are gstreamer0.10-plugins-good and gstreamer0.10-plugins-ugly so they "should" be the proper plugins. I think what might be going on is that one or more of the plugins are not playing nice together](*,)

---

### Post by KompresZor on 2006-11-28
Ok... I fixed it by removing.
```
gstreamer0.10-fluendo-mp3
```
I found the information in this thread [http://ubuntuforums.org/showthread.php?t=270371](http://ubuntuforums.org/showthread.php?t=270371)

---

### Post by KompresZor on 2006-11-29
Fixed is such a relative word... It let GomeBaker work, well sort of, if you call 45 minutes to convert and burn a 74 minute CD working. :rolleyes: 

Serpentine is still broke "Converting files failed"

---

