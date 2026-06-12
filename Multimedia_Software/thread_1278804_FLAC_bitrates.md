---
title: "FLAC bitrates"
date: 2009-09-30
forum: Multimedia Software
---

### Post by Captain_Falafel on 2009-09-30
how can I figure out what bitrate my FLAC files are.. when I right click > properties > audio, I get N/A for bitrate.

---

### Post by andrew.46 on 2009-09-30
Hi Captain,

> **Captain_Falafel said:**
> how can I figure out what bitrate my FLAC files are.. when I right click > properties > audio, I get N/A for bitrate.

If you have a copy of FFmpeg the following syntax should tell you:

```
ffmpeg -i ***[COLOR="Red"]myfile.flac[/COLOR]***
```

I have dug out a flac file to give a better demonstration:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]ffmpeg -i luckynight.flac [/COLOR]**
FFmpeg version SVN-r20088, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Sep 30 2009 10:00:02 with gcc 4.3.3
  configuration: --prefix=/usr --mandir=/usr/man --disable-debug
 --enable-shared --disable-static --enable-postproc --enable-avfilter 
--enable-pthreads --enable-libtheora --enable-libvorbis --enable-x11grab 
--enable-libmp3lame --enable-libx264 --enable-libschroedinger
 --enable-libfaac --enable-libfaad --enable-libopencore-amrnb
 --enable-libopencore-amrwb --enable-version3 --enable-libgsm 
--enable-libspeex --enable-zlib --enable-nonfree --enable-gpl
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.36. 0 / 52.36. 0
  libavformat   52.39. 0 / 52.39. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
[flac @ 0x806a420]MAX_READ_SIZE:5000000 reached
[B][COLOR="Red"]Input #0, flac, from 'luckynight.flac':
  Duration: 00:01:00.48, bitrate: 881 kb/s
    Stream #0.0: Audio: flac, 44100 Hz, 2 channels, s16[/COLOR][/B]
  Metadata
    REPLAYGAIN_TRACK_PEAK: 0.97720337
    REPLAYGAIN_TRACK_GAIN: -4.19 dB
    REPLAYGAIN_ALBUM_PEAK: 0.97720337
    REPLAYGAIN_ALBUM_GAIN: -4.19 dB
    ALBUM           : Treasure Quest Soundtrack
    ARTIST          : Jody Marie Gnant
    DATE            : 1995
    GENRE           : Soundtrack
    COMMENT         : 1-minute song sample demonstrating FLAC compression
    TITLE           : Lucky Night
    TRACKNUMBER     : 9
At least one output file must be specified

```

Andrew

---

### Post by Captain_Falafel on 2009-09-30
> **andrew.46 said:**
> Hi Captain,



If you have a copy of FFmpeg the following syntax should tell you:

```
ffmpeg -i ***[COLOR="Red"]myfile.flac[/COLOR]***
```


Thanks for the quick reply.. 
I tried that, and I get the same thing as I did by going to the properties of the file:

```
ffmpeg -i 04.\ Third\ Eye\ Blind\ -\ Jumper.flac 
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
Input #0, flac, from '04. Third Eye Blind - Jumper.flac':
  Duration: N/A, bitrate: N/A
    Stream #0.0: Audio: flac, 44100 Hz, stereo, s16


```

---

### Post by Rhubarb on 2009-09-30
I don't think it's possible to find out the bitrate of a FLAC file, simply because it's a lossless format.
Sure you can set the compression agressiveness when encoding a file, but that's completely different to setting a compresion level in a lossy audio format.

However, it's still possible to find out the bitrate of a file using old-fasioned means.

All you need is the duration of the flac file in seconds.
And the size of the flac file in kilobits.

Or, if you know the size of the file in megabytes (M):-
size in kilobits = M*1024*8

Then all you have to do is: (size in kilobits) / (duration in seconds)
And voila, you have a pretty good estimate of your bitrate.

---

### Post by Captain_Falafel on 2009-10-03
> **Rhubarb said:**
> I don't think it's possible to find out the bitrate of a FLAC file, simply because it's a lossless format.
Sure you can set the compression agressiveness when encoding a file, but that's completely different to setting a compresion level in a lossy audio format.

However, it's still possible to find out the bitrate of a file using old-fasioned means.

All you need is the duration of the flac file in seconds.
And the size of the flac file in kilobits.

Or, if you know the size of the file in megabytes (M):-
size in kilobits = M*1024*8

Then all you have to do is: (size in kilobits) / (duration in seconds)
And voila, you have a pretty good estimate of your bitrate.


Thanks a lot.. :)

---

