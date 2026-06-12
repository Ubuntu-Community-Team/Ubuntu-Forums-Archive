---
title: "How to play .mpc Musepack"
date: 2010-07-27
forum: Multimedia Software
---

### Post by masque7 on 2010-07-27
I have some mpc Musepack audio files 

My current setup is mpd+ncmpc was just wondering if there are codecs available?

---

### Post by mc4man on 2010-07-27
Well pretty much all players here decode musepack (or at least the samples I have) - vlc, mplayer thru ffmpeg (ffmusepack7). gstreamer players thru the bad  plugin

> Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 0.0 kbit/0.00% (ratio: 0->176400)
Selected audio codec: [ffmusepack7] afm: ffmpeg (Musepack sv7 audio codec)

> doug@doug-desktop1:~$ gst-inspect plugin musepack
Plugin Details:
  Name:			musepack
  Description:		Musepack decoder
  Filename:		/usr/lib/gstreamer-0.10/libgstmusepack.so
  Version:		0.10.19
  License:		LGPL
  Source module:	gst-plugins-bad
  Binary package:	GStreamer Bad Plugins (Ubuntu)
  Origin URL:		[https://launchpad.net/distros/ubuntu/+source/gst-plugins-bad0.10](https://launchpad.net/distros/ubuntu/+source/gst-plugins-bad0.10)

  musepackdec: Musepack decoder


mppenc is in repo or elsewhere  (for encoding

---

