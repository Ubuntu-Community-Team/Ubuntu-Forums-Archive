---
title: "ffmpeg (Could not find codec parameters (Audio: mp1))"
date: 2008-05-05
forum: Multimedia Software
---

### Post by jackal242 on 2008-05-05
Trying to convert a .mkv to a .avi.  I used mkvextract to break them into a H.264 m4v and a mp3 audio file.

When I try to merge them together with ffmpeg it dies with this error:

$ file temp_video.m4v 
temp_video.m4v: JVT NAL sequence, H.264 video @ L 51

$ file temp_audio.mp3 
temp_audio.mp3: MPEG ADTS, layer III, v1, 112 kBits, 44.1 kHz, JntStereo

$ ffmpeg -i temp_audio.mp3 -i temp_video.m4v -vcodec copy foobar.avi
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:25:50, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, mp3, from 'temp_audio.mp3':
  Duration: 00:42:32.3, start: 0.000000, bitrate: 112 kb/s
  Stream #0.0: Audio: mp3, 44100 Hz, stereo, 112 kb/s
[mp3 @ 0xb7edb610]Could not find codec parameters (Audio: mp1, 144 kb/s)
temp_video.m4v: could not find codec parameters

---

