---
title: "aac problems"
date: 2007-02-24
forum: Multimedia &amp; Video
---

### Post by exile on 2007-02-24
I recently reinstalled my machine from Edgy to Edgy and am having a nightmare of a time getting some scripts that I wrote that did work before to work now.

The problem is "Unknown codec 'aac'"

but when I ffmpeg -formats | grep aac

```
$ ffmpeg -formats | grep aac
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Sep 20 2006 00:26:15, gcc: 4.1.2 20060906 (prerelease) (Ubuntu 4.1.1-13ubuntu2)
 D  aac             ADTS AAC

```

As far as I can tell it's there. I've installed gstreamer-plugins-0.8-faac and faad

I can watch m4v that I encoded just a week ago.

To be sure I uninstalled all the plugins and reinstalled, rebooted etc. I installed the good bad and ugly codec sets from universe and multiverse.

This is driving me crazy :( If anything this install is much more vanilla.

If anyone has had this problem and solved I'd be very thankful for any assistance.

Thanks.

---

