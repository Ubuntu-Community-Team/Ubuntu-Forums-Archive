---
title: "Unable to Play .MPG File in Totem in Lubuntu"
date: 2010-11-07
forum: Multimedia Software
---

### Post by maxzorin73 on 2010-11-07
I am having trouble playing .mpg files in Lubuntu 10.10 with Totem. When I try to open the file, I get an error message that says "The playback of this movie requires a MPEG-2 System Stream demuxer plugin which is not installed."

Also, Nautilus does not generate a thumbnail for the .mpg files. (I use Nautilus as my file manager in LXDE because I like the thumbnails feature). My understanding is that Nautilus gets the video thumbnails from Totem somehow.

I do not have these problems in the Ubuntu 10.10 Main Edition. Am I missing a plug-in? If so, which package(s) do I need to install to get Totem and the Nautilus thumbnails to work correctly?

Thanks.

---

### Post by mc4man on 2010-11-07
I would make sure the 'ugly' and 'bad' plugins are installed (there is also a fluendo one though those 2 should be fine
this will check/install what's needed for most all decoding

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly 

```

> gst-inspect plugins mpegstream
Plugin Details:
  Name:			mpegstream
  Description:		MPEG system stream parser
  Filename:		/usr/lib/gstreamer-0.10/libgstmpegstream.so
  Version:		0.10.16
  License:		LGPL
  Source module:	gst-plugins-ugly
  Binary package:	GStreamer Ugly Plugins (Ubuntu)
  Origin URL:		[https://launchpad.net/distros/ubuntu/+source/gst-plugins-ugly0.10](https://launchpad.net/distros/ubuntu/+source/gst-plugins-ugly0.10)

  dvddemux: DVD Demuxer
  mpegdemux: MPEG Demuxer
  mpegparse: MPEG System Parser

  3 features:
  +-- 3 elements

doug@doug-desktop1:~$ gst-inspect plugins mpegdemux2
Plugin Details:
  Name:			mpegdemux2
  Description:		MPEG demuxers
  Filename:		/usr/lib/gstreamer-0.10/libgstmpegdemux.so
  Version:		0.10.20
  License:		unknown
  Source module:	gst-plugins-bad
  Binary package:	GStreamer Bad Plugins (Ubuntu)
  Origin URL:		[https://launchpad.net/distros/ubuntu/+source/gst-plugins-bad0.10](https://launchpad.net/distros/ubuntu/+source/gst-plugins-bad0.10)

  mpegpsdemux: The Fluendo MPEG Program Stream Demuxer
  mpegtsdemux: The Fluendo MPEG Transport stream demuxer
  mpegtsparse: MPEG transport stream parser

  3 features:
  +-- 3 elements

---

### Post by maxzorin73 on 2010-11-07
This worked! Thanks for your help.

---

