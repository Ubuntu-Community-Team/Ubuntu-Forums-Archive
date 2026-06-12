---
title: "Totem plugins (x264) and mplayer plugins"
date: 2008-07-24
forum: Multimedia Software
---

### Post by mikeym on 2008-07-24
Hi,

I'm having problems trying to get x264 files to play on Totem. 

I've had to install x264 myself so that I could encode x264 files. And I can play them in mplayer but they wont play in totem. 

Where are the plugins supposed to go?

I have the following installed:

libx264-54
```
/.
/usr
/usr/lib
/usr/lib/libx264.so.54
/usr/share
/usr/share/doc
/usr/share/doc/libx264-54
/usr/share/doc/libx264-54/copyright
/usr/share/doc/libx264-54/changelog.Debian.gz

```

And:

```
./
usr/
usr/include/
usr/include/x264.h
usr/include/x264_gtk_enum.h
usr/include/x264_gtk.h
usr/share/
usr/share/x264/
usr/share/x264/x264.png
usr/share/locale/
usr/share/locale/fr/
usr/share/locale/fr/LC_MESSAGES/
usr/share/locale/fr/LC_MESSAGES/x264_gtk.mo
usr/share/doc/
usr/share/doc/x264/
usr/share/doc/x264/AUTHORS
usr/share/doc/x264/COPYING
usr/share/doc/x264/doc/
usr/share/doc/x264/doc/regression_test.txt
usr/share/doc/x264/doc/ratecontrol.txt
usr/share/doc/x264/doc/standards.txt
usr/share/doc/x264/doc/vui.txt
usr/share/doc/x264/doc/threads.txt
usr/share/doc/x264/doc/.svn/
usr/share/doc/x264/doc/.svn/format
usr/share/doc/x264/doc/.svn/text-base/
usr/share/doc/x264/doc/.svn/text-base/ratecontrol.txt.svn-base
usr/share/doc/x264/doc/.svn/text-base/threads.txt.svn-base
usr/share/doc/x264/doc/.svn/text-base/vui.txt.svn-base
usr/share/doc/x264/doc/.svn/text-base/regression_test.txt.svn-base
usr/share/doc/x264/doc/.svn/entries
usr/share/doc/x264/doc/.svn/props/
usr/share/doc/x264/doc/.svn/prop-base/
usr/share/doc/x264/doc/.svn/tmp/
usr/share/doc/x264/doc/.svn/tmp/text-base/
usr/share/doc/x264/doc/.svn/tmp/props/
usr/share/doc/x264/doc/.svn/tmp/prop-base/
usr/lib64/
usr/lib64/libx264.so.60
usr/lib64/pkgconfig/
usr/lib64/pkgconfig/x264.pc
usr/lib64/pkgconfig/x264gtk.pc
usr/lib64/libx264gtk.a
usr/lib64/libx264gtk.so.60
usr/lib64/libx264.a
usr/bin/
usr/bin/x264
usr/bin/x264_gtk_encode
usr/lib64/libx264.so
usr/lib64/libx264gtk.so
```

I had to install this one to allow me to encode with mencoder (When it's installed I can encode x264 with mencoder but can't play in mplayer without libx264-54 installed as well. With either or both these files installed I can't play in totem.)

---

### Post by shirilover on 2008-07-24
Decoding of h.264 vieo streams is done with libavcodec.
Totem does not use these libraries, you need gstreamer-0.10-ffmpeg

---

