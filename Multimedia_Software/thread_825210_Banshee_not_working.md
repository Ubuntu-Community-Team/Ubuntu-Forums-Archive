---
title: "Banshee not working"
date: 2008-06-10
forum: Multimedia Software
---

### Post by FunkyJack on 2008-06-10
When I try to play the music on banshee it gives me this error:

```
[Info  01:27:39.266] Running Banshee 0.99.3
[Info  01:27:45.891] All services are started 5.818582s
[Info  01:27:49.622] nereid Client Started
[Error 01:27:52.623] GStreamer resource error: NotFound
[Error 01:27:53.215] GStreamer resource error: NotFound
[Error 01:27:53.822] GStreamer resource error: NotFound
[Error 01:27:54.460] GStreamer resource error: NotFound
[Error 01:27:55.223] GStreamer resource error: NotFound
-||-

```

Anyone knows what it could be?

---

### Post by AOZ on 2008-06-11
looks like you need the GStreamer codec to play whatever your playing. im not sure if its in the repos if not google where to get it

---

### Post by FunkyJack on 2008-06-12
I have all gstreamer codecs installed :(

```

kreso@ubuntu:~$ dpkg -l | grep gstreamer
ii  gstreamer0.10-alsa                         0.10.18-3                                          GStreamer plugin for ALSA
ii  gstreamer0.10-esd                          0.10.7-3ubuntu0.1                                  GStreamer plugin for ESD
ii  gstreamer0.10-ffmpeg                       0.10.3-6                                           FFmpeg plugin for GStreamer
ii  gstreamer0.10-fluendo-mp3                  0.10.7.debian-1                                    Fluendo mp3 decoder GStreamer plugin
ii  gstreamer0.10-fluendo-mpegdemux            0.10.15-1                                          GStreamer plugin for demuxing of MPEG2 strea
ii  gstreamer0.10-fluendo-mpegmux              0.10.2-1                                           GStreamer plugin for muxing of MPEG2 TS stre
ii  gstreamer0.10-gnomevfs                     0.10.18-3                                          GStreamer plugin for GnomeVFS
ii  gstreamer0.10-gnonlin                      0.10.9-1                                           non-linear editing module for GStreamer
ii  gstreamer0.10-pitfdll                      0.9.1.1+cvs20080215-1                              GStreamer plugin for using MS Windows binary
ii  gstreamer0.10-plugins-bad                  0.10.6-5                                           GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-bad-dbg              0.10.6-5                                           GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-bad-doc              0.10.6-5                                           GStreamer documentation for plugins from the
ii  gstreamer0.10-plugins-bad-multiverse       0.10.6-1                                           GStreamer plugins from the "bad" set (Multiv
ii  gstreamer0.10-plugins-bad-multiverse-dbg   0.10.6-1                                           GStreamer plugins from the "bad" set (Multiv
ii  gstreamer0.10-plugins-base                 0.10.18-3                                          GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps            0.10.18-3                                          GStreamer helper programs from the "base" se
ii  gstreamer0.10-plugins-base-dbg             0.10.18-3                                          GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-doc             0.10.18-3                                          GStreamer documentation for plugins from the
ii  gstreamer0.10-plugins-farsight             0.12.5-2ubuntu1                                    plugins for Gstreamer for Audio/Video confer
ii  gstreamer0.10-plugins-good                 0.10.7-3ubuntu0.1                                  GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-good-dbg             0.10.7-3ubuntu0.1                                  GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-good-doc             0.10.7-3ubuntu0.1                                  GStreamer documentation for plugins from the
ii  gstreamer0.10-plugins-ugly                 0.10.7-3                                           GStreamer plugins from the "ugly" set
ii  gstreamer0.10-plugins-ugly-dbg             0.10.7-3                                           GStreamer plugins from the "ugly" set
ii  gstreamer0.10-plugins-ugly-doc             0.10.7-3                                           GStreamer documentation for plugins from the
ii  gstreamer0.10-plugins-ugly-multiverse      0.10.7-1                                           GStreamer plugins from the "ugly" set (Multi
ii  gstreamer0.10-plugins-ugly-multiverse-dbg  0.10.7-1                                           GStreamer plugins from the "ugly" set (Multi
ii  gstreamer0.10-pulseaudio                   0.9.7-2                                            GStreamer plugin for PulseAudio
ii  gstreamer0.10-sdl                          0.10.6-5                                           GStreamer plugin for SDL output
ii  gstreamer0.10-tools                        0.10.18-4ubuntu1                                   Tools for use with GStreamer
ii  gstreamer0.10-x                            0.10.18-3                                          GStreamer plugins for X11 and Pango
ii  libgstreamer-plugins-base0.10-0            0.10.18-3                                          GStreamer libraries from the "base" set
ii  libgstreamer-plugins-base0.10-dev          0.10.18-3                                          GStreamer development files for libraries fr
ii  libgstreamer-plugins-pulse0.10-0           0.9.7-2                                            GStreamer plugin for PulseAudio (transitiona
ii  libgstreamer0.10-0                         0.10.18-4ubuntu1                                   Core GStreamer libraries and elements
ii  libgstreamer0.10-dev                       0.10.18-4ubuntu1                                   GStreamer core development files
ii  totem-gstreamer                            2.22.1-0ubuntu2                                    A simple media player for the Gnome desktop 


```

---

### Post by asuastrophysics on 2009-11-22
I have the exact same problem, and it all started after upgrading to Karmic.

Upon concluding this, I have decided that the best workaround is to never upgrade. Ever. 
 
Stay with your release as long as you can, because with every subsequent release, the same old bugs come back...go figure. :D

---

### Post by asuastrophysics on 2009-11-22
I just tried installing and reinstalling to see if that would remedy this.

Nope!

Banshee is garbage.

---

