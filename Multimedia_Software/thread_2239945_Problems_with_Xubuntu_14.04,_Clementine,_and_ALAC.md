---
title: "Problems with Xubuntu 14.04, Clementine, and ALAC"
date: 2014-08-16
forum: Multimedia Software
---

### Post by mackenzie-vogt on 2014-08-16
All,

I was wondering if you could help me with me a persistent issue I am facing as I cannot solve it on my own or through google-fu.

Running Xubuntu 14.04, with Clementine 1.2 as my preferred media player.  For the life of me, I cannot get my ALAC (Apple Lossless Audio Codec, left over from my time as an iDevice user) files (stored as .m4a, MPEG-4 audio) to play without an error that simply says "Your GStreamer installation is missing a plug-in.".

I was wondering if anyone has experienced this and if they could point me to what package needs to be installed.  Here are the gstreamer packages I currently have on my system:

```
ii  gstreamer0.10-alsa:amd64                    0.10.36-1.1ubuntu2                     amd64        GStreamer plugin for ALSA
ii  gstreamer0.10-fluendo-mp3:amd64             0.10.23.debian-3                       amd64        Fluendo mp3 decoder GStreamer 0.10 plugin
ii  gstreamer0.10-nice:amd64                    0.1.4-1                                amd64        ICE library (GStreamer 0.10 plugin)
ii  gstreamer0.10-plugins-bad:amd64             0.10.23-7.2ubuntu1                     amd64        GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-bad-multiverse        0.10.21-1ubuntu3                       amd64        GStreamer plugins from the "bad" set (Multiverse Variant)
ii  gstreamer0.10-plugins-base:amd64            0.10.36-1.1ubuntu2                     amd64        GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps             0.10.36-1.1ubuntu2                     amd64        GStreamer helper programs from the "base" set
ii  gstreamer0.10-plugins-good:amd64            0.10.31-3+nmu1ubuntu5                  amd64        GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-ugly:amd64            0.10.19-2ubuntu5                       amd64        GStreamer plugins from the "ugly" set
ii  gstreamer0.10-pulseaudio:amd64              0.10.31-3+nmu1ubuntu5                  amd64        GStreamer plugin for PulseAudio
ii  gstreamer0.10-tools                         0.10.36-1.2ubuntu3                     amd64        Tools for use with GStreamer
ii  gstreamer0.10-x:amd64                       0.10.36-1.1ubuntu2                     amd64        GStreamer plugins for X11 and Pango
ii  gstreamer1.0-fluendo-mp3:amd64              0.10.23.debian-3                       amd64        Fluendo mp3 decoder GStreamer 1.0 plugin
ii  gstreamer1.0-libav:amd64                    1.2.4-1~ubuntu1                        amd64        libav plugin for GStreamer
ii  gstreamer1.0-plugins-bad:amd64              1.2.4-1~ubuntu1                        amd64        GStreamer plugins from the "bad" set
ii  gstreamer1.0-plugins-bad-faad:amd64         1.2.4-1~ubuntu1                        amd64        GStreamer faad plugin from the "bad" set
ii  gstreamer1.0-plugins-bad-videoparsers:amd64 1.2.4-1~ubuntu1                        amd64        GStreamer videoparsers plugin from the "bad" set
ii  gstreamer1.0-plugins-base:amd64             1.2.4-1~ubuntu1                        amd64        GStreamer plugins from the "base" set
ii  gstreamer1.0-plugins-good:amd64             1.2.4-1~ubuntu1                        amd64        GStreamer plugins from the "good" set
ii  gstreamer1.0-plugins-ugly:amd64             1.2.3-2build1                          amd64        GStreamer plugins from the "ugly" set
ii  gstreamer1.0-pulseaudio:amd64               1.2.4-1~ubuntu1                        amd64        GStreamer plugin for PulseAudio
ii  gstreamer1.0-tools                          1.2.4-0ubuntu1                         amd64        Tools for use with GStreamer
ii  gstreamer1.0-x:amd64                        1.2.4-1~ubuntu1                        amd64        GStreamer plugins for X11 and Pango



```

Thanks in advance for your help :cool:

---

### Post by mc4man on 2014-08-17
clementine is still using gstreamer0.10 & there is no longer a 0.10 ffmpeg plugin available in 14.04
you can get it here, either by adding the ppa & then installing gstreamer0.10-ffmpeg  or just downloading the package & installing the package itself, your choice..
[https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)

For just downloading the package, install with gdebi, Software-center or if all deps are already installed dpkg is ok (you have all deps installed I believe
64 bit
```
wget https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media/+build/5803642/+files/gstreamer0.10-ffmpeg_0.10.13-5ubuntu1%7Etrusty2_amd64.deb
```

32bit
```
wget https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media/+build/5803643/+files/gstreamer0.10-ffmpeg_0.10.13-5ubuntu1%7Etrusty2_i386.deb
```

---

### Post by mackenzie-vogt on 2014-08-17
mc4man,

Thank you so much.  This fixed it.  Really appreciated!! :mrgreen:

---

### Post by Yellow Pasque on 2014-08-18
I chose to convert my ALAC -> FLAC (though I only had a limited number of them). ffmpeg/avconv makes short work of it.
Something to consider...

---

