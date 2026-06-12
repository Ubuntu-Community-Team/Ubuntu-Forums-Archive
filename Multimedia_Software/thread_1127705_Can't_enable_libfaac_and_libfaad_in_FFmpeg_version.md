---
title: "Can't enable libfaac and libfaad in FFmpeg version SVN-r18405"
date: 2009-04-16
forum: Multimedia Software
---

### Post by V. Wayne on 2009-04-16
I have tried and can't enable libfaac and libfaad in FFmpeg version SVN-r18405. I have the both packages installed.

Any suggestions?

Here is the information;

user@Office-Laptop:/usr/local/src/ffmpeg$ ffmpeg -i
FFmpeg version SVN-r18405, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-libmp3lame --enable-libvorbis --disable-mmx --enable-shared --enable-libamr-nb --enable-libamr-wb --enable-nonfree --enable-libtheora
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.25. 0 / 52.25. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Apr 16 2009 18:45:43, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)

user@Office-Laptop:/usr/local/src/ffmpeg$ ldd ./ffmpeg
	linux-gate.so.1 =>  (0xb7f09000)
	libavdevice.so.52 => /usr/local/lib/libavdevice.so.52 (0xb7eef000)
	libavformat.so.52 => /usr/local/lib/libavformat.so.52 (0xb7df6000)
	libavcodec.so.52 => /usr/local/lib/libavcodec.so.52 (0xb76e1000)
	libavutil.so.50 => /usr/local/lib/libavutil.so.50 (0xb76d0000)
	libswscale.so.0 => /usr/local/lib/libswscale.so.0 (0xb76a7000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7682000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7533000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb751d000)
	libamrnb.so.3 => /usr/local/lib/libamrnb.so.3 (0xb74e0000)
	libamrwb.so.3 => /usr/local/lib/libamrwb.so.3 (0xb74b4000)
	libmp3lame.so.0 => /usr/local/lib/libmp3lame.so.0 (0xb7425000)
	libtheora.so.0 => /usr/local/lib/libtheora.so.0 (0xb73de000)
	libvorbisenc.so.2 => /usr/local/lib/libvorbisenc.so.2 (0xb72e3000)
	libvorbis.so.0 => /usr/local/lib/libvorbis.so.0 (0xb72ba000)
	/lib/ld-linux.so.2 (0xb7f0a000)
	libogg.so.0 => /usr/local/lib/libogg.so.0 (0xb72b5000)

---

### Post by FakeOutdoorsman on 2009-04-16
You didn't configure FFmpeg to compile with libfaac and libfaad:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Make sure to uninstall FFmpeg and then run "make distclean" in your ffmpeg source directory before running ./configure.

---

### Post by andrew.46 on 2009-04-16
Hi FakeOutdoorsman,

> **FakeOutdoorsman said:**
> You didn't configure FFmpeg to compile with libfaac and libfaad

This highlights one of the huge differences between configuring the svn MPlayer and the svn FFmpeg. FFmpeg asks that you carefully ask for each option that you want at ./configure while MPlayer, except for a few options, demands that you *don't* do this. Two very different approaches, bound to lead to some confusion of course :-).

Andrew

---

### Post by V. Wayne on 2009-04-17
Thanks guys, I'll make the correction.

---

