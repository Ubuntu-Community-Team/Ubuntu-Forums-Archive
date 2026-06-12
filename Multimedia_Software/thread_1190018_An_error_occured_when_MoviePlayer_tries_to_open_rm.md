---
title: "An error occured when MoviePlayer tries to open rmvb file"
date: 2009-06-17
forum: Multimedia Software
---

### Post by lidengdeng on 2009-06-17
Hi, 

My Totem Movie Player 2.22 met a error info when tries to open an rmvb file. The error message is below:

An error occurred 
GStreamer encountered a general stream error

So any help? Thanks.

ps: it work well while playing avi files.

---

### Post by jerrrys on 2009-06-17
here's some interesting (and incomplete) reading

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/242351](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/242351)

also

[http://www.google.com/search?q=totem+movie+player+rmvb+file&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=totem+movie+player+rmvb+file&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

and

[http://www.google.com/search?q=rmvb+file&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=rmvb+file&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by lidengdeng on 2009-06-18
Thanks for your suggestion.

Now the Realplayer is working well on these rmvb files.

---

### Post by jerrrys on 2009-06-18
:)

---

### Post by colau on 2009-09-01
> **lidengdeng said:**
> Hi, 

My Totem Movie Player 2.22 met a error info when tries to open an rmvb file. The error message is below:

An error occurred 
GStreamer encountered a general stream error

So any help? Thanks.

ps: it work well while playing avi files.
Totem can play .rm/.rmvb files.
Did you install these?
```

gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly
w32codecs

```

---

### Post by levells on 2009-10-21
I have the exact same problem.  It hives me the same error.  The thing is, it worked fine 3 days ago.  My guess is that something got uninstalled, possibly when I tried openshot.
I'm not sure what else to put here, except a list of the plugins.  I like Totem's setup and add in the fact that other vido players delay the sound, so I'd like to try and keep Totem, if possible.
```
dpkg -l | grep gstreamer
ii  bluez-gstreamer                            4.32-0ubuntu4.1                           Bluetooth gstreamer support
ii  gstreamer0.10-alsa                         0.10.24-1~pidgin1.9.04                    GStreamer plugin for ALSA
ii  gstreamer0.10-ffmpeg                       0.10.6.2-1ubuntu2                         FFmpeg plugin for GStreamer
ii  gstreamer0.10-gnomevfs                     0.10.24-1~pidgin1.9.04                    GStreamer plugin for GnomeVFS
ii  gstreamer0.10-gnonlin                      0.10.10-2                                 non-linear editing module for GStreamer
ii  gstreamer0.10-nice                         0.0.9-1~pidgin1.9.04                      ICE library (GStreamer plugin)
ii  gstreamer0.10-pitfdll                      0.9.1.1+cvs20080215-1ubuntu1              GStreamer plugin for using MS Windows binary codecs
ii  gstreamer0.10-plugins-bad                  0.10.13-1ubuntu1~pidgin1.9.04             GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-bad-multiverse       0.10.11-0ubuntu1                          GStreamer plugins from the "bad" set (Multiverse Variant)
ii  gstreamer0.10-plugins-bad-multiverse-dbg   0.10.11-0ubuntu1                          GStreamer plugins from the "bad" set (Multiverse Variant)
ii  gstreamer0.10-plugins-base                 0.10.24-1~pidgin1.9.04                    GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps            0.10.24-1~pidgin1.9.04                    GStreamer helper programs from the "base" set
ii  gstreamer0.10-plugins-good                 0.10.15-2ubuntu1~pidgin4.9.04             GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-ugly                 0.10.12-1~pidgin1.9.04                    GStreamer plugins from the "ugly" set
ii  gstreamer0.10-plugins-ugly-multiverse      0.10.7-2                                  GStreamer plugins from the "ugly" set (Multiverse Variant)
ii  gstreamer0.10-plugins-ugly-multiverse-dbg  0.10.7-2                                  GStreamer plugins from the "ugly" set (Multiverse Variant)
ii  gstreamer0.10-pulseaudio                   0.10.15-2ubuntu1~pidgin4.9.04             GStreamer plugin for PulseAudio
ii  gstreamer0.10-schroedinger                 1.0.5-1                                   GStreamer plugin for encoding/decoding of Dirac video streams
ii  gstreamer0.10-tools                        0.10.24-1~pidgin1.9.04                    Tools for use with GStreamer
ii  gstreamer0.10-x                            0.10.24-1~pidgin1.9.04                    GStreamer plugins for X11 and Pango
ii  libgstreamer-plugins-base0.10-0            0.10.24-1~pidgin1.9.04                    GStreamer libraries from the "base" set
ii  libgstreamer-plugins-base0.10-dev          0.10.24-1~pidgin1.9.04                    GStreamer development files for libraries from the "base" set
ii  libgstreamer0.10-0                         0.10.24-1~pidgin1.9.04                    Core GStreamer libraries and elements
ii  libgstreamer0.10-dev                       0.10.24-1~pidgin1.9.04                    GStreamer core development files
ii  totem-gstreamer                            2.26.1-0ubuntu5                           A simple media player for the GNOME desktop based on GStreamer
```

---

