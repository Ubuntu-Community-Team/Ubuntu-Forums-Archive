---
title: "Converter for MS Mpeg4"
date: 2010-08-11
forum: Multimedia Software
---

### Post by tragedy0607 on 2010-08-11
Hi All,

I am trying to find a way to convert MS Mpeg4 files to a format that is playable on Totem or any of the media players for Ubuntu.

I have tried many converters, even trying ones in Windows (I really didn't want to but thought I would give it a shot)

I have installed all the limited FFMPEG and x2.64 restricted and limited libraries.  I have all the multiverse and universe repositories.

I have tried WINFF, Avidemux, DeVeDe but to no avail and now I am tearing my hair out.

Totem cannot find any plugins suitable.

The codecs needed are below....

audio/x-gst-fourcc-enca
video/x-gst-fourcc-encv

Can anyone give me any suggestions?  I am using 9.04.

Thanks in advance

---

### Post by JBAlaska on 2010-08-11
Using the samples ( FourCCs: MPG4, MP41, MP42, MP43, DIV3, WMV7, WMV8, AP41, COL1 ) from this [List](http://wiki.multimedia.cx/index.php?title=Microsoft_MPEG-4) I was able to play all of them with mplayer and the VLC plugin for FireFox.

You might have a look at [MEncoder](http://web.njit.edu/all_topics/Prog_Lang_Docs/html/mplayer/encoding.html)

---

### Post by FakeOutdoorsman on 2010-08-11
I think the *gstreamer0.10-ffmpeg* package might allow you to watch this format with Totem.

---

