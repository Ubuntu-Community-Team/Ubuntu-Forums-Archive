---
title: "ffmpeg and libfaac"
date: 2008-04-13
forum: Multimedia &amp; Video
---

### Post by akc42 on 2008-04-13
I have just switched over from Debian (unstable) in order to have a more stable environment for my desktop.  However there is one thing that I could do before, which I can't seem to do now

I have been encoding videos for my ipod Nano with the following command

ffmpeg -i "$1" -f mp4 -vcodec mpeg4 -b 600k -r 29.97 -acodec libfaac -ab 64 -ac 2 -s 320x240 "$2.mp4"

I have installed the package libfaac0, but when I attempt to encode a video I get

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.97 (30000/1001)
Input #0, flv, from 'iam5.flv':
  Duration: 00:02:54.6, start: 0.000000, bitrate: 56 kb/s
  Stream #0.0: Video: flv, yuv420p, 320x240, 29.97 fps(r)
  Stream #0.1: Audio: mp3, 22050 Hz, mono, 56 kb/s
Unknown codec 'libfaac'


In otherwords, it doesn't know about libfaac.  Is there something else I need to do to get libfaac?

---

### Post by xc3RnbFO8P on 2008-04-13
This is just a thought, you are using  **FFmpeg2theora** I think you should be using **FFmpeg**.
search in Synaptic Package Manager: **ffmpeg **

---

### Post by mc4man on 2008-04-13
If your using the repo version of ffmpeg I'm not too sure faac support is enabled.Looking at the repo source there isn't anything in rules enabling it and the readme says
> Summary of the patent issues with ffmpeg
========================================

   The only patents related to ffmpeg which seem to be enforced against open
source software cover the following codec technologies and file formats:

   * MP3 encoding
   * AAC decoding and encoding
   * the ASF file format

   I did not activate MP3 encoding (through LAME) in libavcodec, nor AAC
support (through FAAC/FAAD). However, since I have found no real enforcement
of the mysterious ASF file format patents, I did not deactivate ASF support in
libavformat. See more details in the patents.txt file.
you might want to ck. that out 1st. before exploring other reasons

sidenote interesting alternatives
[http://h264enc.sourceforge.net/](http://h264enc.sourceforge.net/)
[http://xvidenc.sourceforge.net/](http://xvidenc.sourceforge.net/)
[http://divxenc.sourceforge.net/](http://divxenc.sourceforge.net/)

---

