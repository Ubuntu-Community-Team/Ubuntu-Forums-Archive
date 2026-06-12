---
title: "[Edgy] quodlibet won't play oggs or flacs, can't find what packages are missing"
date: 2006-10-10
forum: Multimedia &amp; Video
---

### Post by est on 2006-10-10
Hello,
I've tried this with quodlibet 0.23 and someone's svn debs.

quodlibet on Edgy is not reporting support for oggs nor flacs. As far as I know this support should be provided through python-gst. If someone with a working set up could look over the packages I have and tell me where theirs are different I'd be very grateful.

From dpkg:
```

ii  gstreamer0.10-x                        0.10.10-1ubuntu1                     GStreamer plugins for X11 and Pango

ii  gstreamer0.10-plugins-good             0.10.4-0ubuntu3                      GStreamer plugins from the "good" set

ii  python-gst0.10                         0.10.5-5ubuntu1                      generic media-playing framework (Python bind

ii  python-pyogg                           1.3-1.1ubuntu2                       A Python interface to the Ogg library

ii  python-flac                            0.0.4-1                              Free Lossless Audio Codec [Python bindings]

```

Running quodlibet:
```

$ quodlibet
Supported formats: mod, mp3, mp4, mpc, trueaudio, wav, wavpack, xiph

```

Sucks, eh? Anything obviously wrong? More info needed?

---

### Post by hugmenot on 2006-10-12
No, it doesn&#8217;t suck. I filed a ticket to explain that using that name is obscure but they wouldn&#8217;t listen.
You see "xiph" on that line, it subsumes all of Ogg Vorbis, (Ogg) FLAC, (Ogg) Speex, and Ogg Theora.

So, they actually are supported. Did you try to actually add and play a file?

---

