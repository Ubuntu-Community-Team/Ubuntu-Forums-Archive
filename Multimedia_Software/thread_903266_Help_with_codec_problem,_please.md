---
title: "Help with codec problem, please"
date: 2008-08-28
forum: Multimedia Software
---

### Post by daka on 2008-08-28
SOLVED!!  ..... " Re: ffmpeg and aac audio
This issue was resolved by a (later) update of libavcodec etc., while retaining "Medibuntu" earlier version of Ffmpeg"
------------------------------------------------

I have encountered a codec problem while trying to convert .Mod files to .Mov.  This is new!  I didn have this problem before reinstalling the Ubuntu operating system.  I am a bit baffled because the .Mod files can be reproduced by Xine Movie Player... doesn this indicate that the codec is available in the laptop?

Here is the terminal output:

daka@daka-TB:~/Desktop$ ffmpeg -i MOV008.MOD -g 60 -vcodec msmpeg4v2 -acodec pcm_u8 MOV024.avi
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Aug 10 2008 11:11:16, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, mpeg, from 'MOV008.MOD':
  Duration: 00:00:48.7, start: 0.251978, bitrate: 9205 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576, 8500 kb/s, 25.00 fps(r)
  Stream #0.1[0x80]: Audio: 0x0000, 48000 Hz, stereo, 384 kb/s
Output #0, avi, to 'MOV024.avi':
  Stream #0.0: Video: msmpeg4v2, yuv420p, 720x576, q=2-31, 200 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: pcm_u8, 48000 Hz, stereo, 768 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec (id=86020) for input stream #0.1
daka@daka-TB:~/Desktop$ 


Any help appreciated

Daka

---

