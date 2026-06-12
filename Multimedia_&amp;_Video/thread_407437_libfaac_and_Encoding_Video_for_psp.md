---
title: "libfaac and Encoding Video for psp"
date: 2007-04-12
forum: Multimedia &amp; Video
---

### Post by igb on 2007-04-12
I am trying to encode some videos for a psp.  I am using ffmpeg compiled from cvs, so it includes all the restricted options. The command line I am using is:

```
ffmpeg -y -i "Infile" -f psp -s 320x240 -r 14.985 -b 384 -ar 2400 -ab 64 -acodec aac -ac 2 outfile.mp4
```

I get the following error:

```
ian@hannah:~/dvd$ ffmpeg -y -i "Doctor Who - 2006-04-29, 7-20 PM - School Reunion.mpg" -f psp -s 320x240 -r 14.985 -b 384 -ar 2400 -ab 64 -acodec aac -ac 2 dr_who.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-pthreads
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan  8 2007 14:47:03, gcc: 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
Input #0, mpegts, from 'Doctor Who - 2006-04-29, 7-20 PM - School Reunion.mpg':
  Duration: 00:45:29.6, start: 44000.084467, bitrate: 4957 kb/s
  Stream #0.0[0x258]: Video: mpeg2video, yuv420p, 720x576, 15000 kb/s, 25.00 fps(r)
  Stream #0.1[0x259](eng): Audio: mp2, 48000 Hz, stereo, 256 kb/s
  Stream #0.2[0x25a](eng): Audio: mp2, 48000 Hz, mono, 64 kb/s
  Stream #0.3[0x25b](eng): Subtitle: dvbsub
Output #0, psp, to 'dr_who.mp4':
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, q=2-31, 384 kb/s, 14.99 fps(c)
  Stream #0.1: Audio: aac, 2400 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[aac @ 0x950db0]libfaac doesn't support this output format!
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

```

It looks as though the version of libfaac in Edgy doesn't support  aac, although ffmpeg -formats shows that my version of ffmpeg does support aac. Any ideas as to how I can enable aac support in libfaac?

Ian.

---

### Post by zcold on 2007-10-24
try setting the bitrate higher...  128 kb/s and an audio sampling frequency of 44100.

---

