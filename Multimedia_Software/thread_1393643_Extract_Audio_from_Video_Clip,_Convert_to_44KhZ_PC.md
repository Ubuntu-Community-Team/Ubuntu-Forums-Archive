---
title: "Extract Audio from Video Clip, Convert to 44KhZ PCM WAV"
date: 2010-01-29
forum: Multimedia Software
---

### Post by walruspanzer on 2010-01-29
I am trying to change the voices on my garmin GPS device. The voice studio software will only import 44KhZ PCM WAV files. I tried extracting the audio with Avidemux but saving the file as *.wav doesn't seem to work. 

Is there a way to extract the audio from a video, trim it, and convert it to 44KhZ PCM wav format?

---

### Post by andrew.46 on 2010-01-29
Hi walruspanzer,

> **walruspanzer said:**
> Is there a way to extract the audio from a video, trim it, and convert it to 44KhZ PCM wav format?

Have you considered using FFmpeg? It has huge possibilities for extracting sound and converting to pcm. PCM formats that FFmpeg can read and encode:

```

andrew@skamandros~$ **[COLOR="Red"]ffmpeg -codecs | grep 'DEA *pcm'[/COLOR]**
FFmpeg version SVN-r21450, Copyright (c) 2000-2010 Fabrice Bellard, et al.
  built on Jan 26 2010 20:31:23 with gcc 4.3.3
  configuration: --prefix=/usr --mandir=/usr/man --enable-shared 
--disable-static --enable-postproc --enable-avfilter --enable-pthreads 
--enable-libtheora --enable-libvorbis --enable-x11grab 
--enable-libmp3lame --enable-libx264 --enable-libschroedinger 
--enable-libfaac --enable-libfaad --enable-libopencore-amrnb 
--enable-libopencore-amrwb --enable-version3 --enable-libspeex 
--enable-zlib --enable-nonfree --enable-gpl
  libavutil     50. 7. 0 / 50. 7. 0
  libavcodec    52.48. 0 / 52.48. 0
  libavformat   52.47. 0 / 52.47. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.17. 0 /  1.17. 0
  libswscale     0. 9. 0 /  0. 9. 0
  libpostproc   51. 2. 0 / 51. 2. 0
 DEA    pcm_alaw        PCM A-law
 DEA    pcm_f32be       PCM 32-bit floating point big-endian
 DEA    pcm_f32le       PCM 32-bit floating point little-endian
 DEA    pcm_f64be       PCM 64-bit floating point big-endian
 DEA    pcm_f64le       PCM 64-bit floating point little-endian
 DEA    pcm_mulaw       PCM mu-law
 DEA    pcm_s16be       PCM signed 16-bit big-endian
 DEA    pcm_s16le       PCM signed 16-bit little-endian
 DEA    pcm_s24be       PCM signed 24-bit big-endian
 DEA    pcm_s24daud     PCM D-Cinema audio signed 24-bit
 DEA    pcm_s24le       PCM signed 24-bit little-endian
 DEA    pcm_s32be       PCM signed 32-bit big-endian
 DEA    pcm_s32le       PCM signed 32-bit little-endian
 DEA    pcm_s8          PCM signed 8-bit
 DEA    pcm_u16be       PCM unsigned 16-bit big-endian
 DEA    pcm_u16le       PCM unsigned 16-bit little-endian
 DEA    pcm_u24be       PCM unsigned 24-bit big-endian
 DEA    pcm_u24le       PCM unsigned 24-bit little-endian
 DEA    pcm_u32be       PCM unsigned 32-bit big-endian
 DEA    pcm_u32le       PCM unsigned 32-bit little-endian
 DEA    pcm_u8          PCM unsigned 8-bit
 DEA    pcm_zork        PCM Zork

```

There is a great guide here to show several different ways to get the best possible version of FFmpeg up and going:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

If you are interested you could get this installed and interrogate one of your videos as follows:
```

ffmpeg -i ***[COLOR="Red"]my_video.mp4[/COLOR]***
```

where of course you must substitute your own filename for 'my_video.mp4'. Post the command + full terminal output here and I am sure you can get some assistance with the extraction and conversion to pcm.

All the best,'

Andrew

---

