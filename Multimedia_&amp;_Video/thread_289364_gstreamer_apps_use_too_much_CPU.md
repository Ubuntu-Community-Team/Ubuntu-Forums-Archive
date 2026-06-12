---
title: "gstreamer apps use too much CPU"
date: 2006-10-30
forum: Multimedia &amp; Video
---

### Post by waltervalderrama on 2006-10-30
I posted several weeks ago but none seemed to help me. Please, I want to know what is the problem. I have a P4 2.0 GHz, 512 MB RAM, GeForce MX 440 and CMI PCI sound card. Some time ago, I have noticed gstreamer apps consume too much CPU. Running rhythmbox shows when "top" 47% of CPU, and when I open more apps, sound fails and crashes. What could be the problem. I didn't have that problem before. Any idea?

I wait your suggestions please.......

---

### Post by tommcd on 2006-10-31
If you are using visualizations with your audio apps, turn them off. Visualizations do tend to consume a lot of CPU power. Other than that, I suppose it could be the driver for your sound card that perhaps is hogging your CPU.

---

### Post by jvolkman on 2006-10-31
I was experiencing rather high CPU usage with gstreamer apps (15-20%). I tracked it down to the Fluendo MP3 plugin.
```

sudo apt-get remove gstreamer0.10-fluendo-mp3
sudo apt-get install gstreamer0.10-plugins-ugly

```

This brought CPU usage back down to a reasonable level.

---

### Post by uboltun on 2006-12-12
> **jvolkman said:**
> I was experiencing rather high CPU usage with gstreamer apps (15-20%). I tracked it down to the Fluendo MP3 plugin.
```

sudo apt-get remove gstreamer0.10-fluendo-mp3
sudo apt-get install gstreamer0.10-plugins-ugly

```

This brought CPU usage back down to a reasonable level.

I have the same problem xmms plays fine , but rythmbox uses too much cpu. 
I do not have fluendo , but have plugins-ugly installed.

:~$ dpkg -l| grep gstreamer
ii  gstreamer0.10-alsa                     0.10.7-0ubuntu5                         GStreamer plugin for ALSA
ii  gstreamer0.10-esd                      0.10.3-0ubuntu4                         GStreamer plugin for ESD
ii  gstreamer0.10-ffmpeg                   0.10.1-0ubuntu2                         FFmpeg plugin for GStreamer
ii  gstreamer0.10-gl                       0.10.3-0ubuntu3                         GStreamer plugin for OpenGL output
ii  gstreamer0.10-gnomevfs                 0.10.7-0ubuntu5                         GStreamer plugin for GnomeVFS
ii  gstreamer0.10-plugins-bad              0.10.3-0ubuntu3                         GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-bad-multiverse   0.10.3-3                                GStreamer plugins from the "bad" set (Multiverse Variant
ii  gstreamer0.10-plugins-base             0.10.7-0ubuntu5                         GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps        0.10.7-0ubuntu5                         GStreamer helper programs from the "base" set
ii  gstreamer0.10-plugins-good             0.10.3-0ubuntu4                         GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-ugly             0.10.3-0ubuntu3                         GStreamer plugins from the "ugly" set
ii  gstreamer0.10-plugins-ugly-multiverse  0.10.3-2                                GStreamer plugins from the "ugly" set (Multiverse Varian
ii  gstreamer0.10-tools                    0.10.6-0ubuntu2                         Tools for use with GStreamer
ii  gstreamer0.10-x                        0.10.7-0ubuntu5                         GStreamer plugins for X11 and Pango
ii  gstreamer0.8-lame                      0.8.12-1                                LAME encoder plugin for GStreamer
ii  gstreamer0.8-misc                      0.8.12-1ubuntu2                         Collection of various GStreamer plugins
ii  libgstreamer-gconf0.8-0                0.8.12-1ubuntu2                         GConf support for GStreamer
ii  libgstreamer-plugins-base0.10-0        0.10.7-0ubuntu5                         GStreamer libraries from the "base" set
ii  libgstreamer-plugins0.8-0              0.8.12-1ubuntu2                         Various GStreamer libraries and library plugins
ii  libgstreamer0.10-0                     0.10.6-0ubuntu2                         Core GStreamer libraries and elements
ii  libgstreamer0.8-0                      0.8.12-1ubuntu1                         Core GStreamer libraries, plugins, and utilities
rc  totem-gstreamer                        1.4.1-0ubuntu4                          A simple media player for the Gnome desktop based on gst

---

### Post by sancheztavo on 2007-03-07
Thanks! 
those *ugly* plugins aren't that ugly after all, CPU usage using both rhythmbox or listen decreased significantly.

---

