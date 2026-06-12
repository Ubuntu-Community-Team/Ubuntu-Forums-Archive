---
title: "Problem with mp4ize"
date: 2008-11-07
forum: Multimedia Software
---

### Post by rudeboyskunk on 2008-11-07
So I tried to use mp4ize to convert some episodes of The Office into mp4 format so I could put them on my iPod.  However, it doesn't seem to work.  This is the output I get in a terminal:

rudeboyskunk@kimchi:/media/Seagate 100/Videos/The Office/Season 3$ mp4ize 01.\ Gay\ Witch\ Hunt.avi 
0.00% | FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)

Seems stream 0 codec frame rate differs from container frame rate: 2997.00 (2997/1) -> 23.98 (24000/1001)
Input #0, avi, from '01. Gay Witch Hunt.avi':
  Duration: 00:21:21.0, start: 0.000000, bitrate: 1422 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 624x352, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
Unknown codec 'xvid'
0.00% | FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)

Seems stream 0 codec frame rate differs from container frame rate: 2997.00 (2997/1) -> 23.98 (24000/1001)
Input #0, avi, from '01. Gay Witch Hunt.avi':
  Duration: 00:21:21.0, start: 0.000000, bitrate: 1422 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 624x352, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
Unknown codec 'libxvid'
0.00% | FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)

Seems stream 0 codec frame rate differs from container frame rate: 2997.00 (2997/1) -> 23.98 (24000/1001)
Input #0, avi, from '01. Gay Witch Hunt.avi':
  Duration: 00:21:21.0, start: 0.000000, bitrate: 1422 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 624x352, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
Unknown codec 'libxvid'
rudeboyskunk@kimchi:/media/Seagate 100/Videos/The Office/Season 3$

---

### Post by cesera on 2008-11-07
I have exactly the same problem. On Kubuntu 8.10. If I use the -v switch on mp4ize it tells me it is running the following command:

```
ffmpeg -i 'test-002.avi' -f mp4 -vcodec xvid -maxrate 1000 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -s 320x188 -padtop 26 -padbottom 26 -ab 128 -b 400 'test-002.mp4' 2>&1 
```

when this fails it then tries the same with libxvid instead of xvid. If anyone could help out with this, that would be great.

---

### Post by cesera on 2008-11-07
Just managed to get it going, not sure yet if it will work completely, but with the following additions it seems to run:

```
sudo apt-get installlibavcodec-unstripped-51 libavdevice-unstripped-52 libavformat-unstripped-52 libavutil-unstripped-49 libpostproc-unstripped-51 libswscale-unstripped-0

```Thank to 'mr_pouit' in this thread:

[http://ubuntuforums.org/showthread.php?p=6126789#post6126789](http://ubuntuforums.org/showthread.php?p=6126789#post6126789)

---

