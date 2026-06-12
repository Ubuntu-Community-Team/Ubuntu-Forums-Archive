---
title: "ia32-libs missing"
date: 2009-04-03
forum: Multimedia Software
---

### Post by slammed87d21 on 2009-04-03
I was going through installing codecs and such, and when I entered 

> sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea6-plugin libavcodec-unstripped-51 libmp3lame0 non-free-codecs openjdk-6-jre unrar

terminal said "E: Couldn't find package ia32-libs". I found and downloaded the ia32-libs deb file, and upon trying to install it, it says wrong architecture. Any suggestions on how to fix this? I've never had this problem with 8.10 before.

---

### Post by slammed87d21 on 2009-04-04
Anyone?

---

### Post by comandrei on 2009-04-04
ia32-libs is a package for amd64 architecture. You don't need it if you're on a 32 bit system.

---

