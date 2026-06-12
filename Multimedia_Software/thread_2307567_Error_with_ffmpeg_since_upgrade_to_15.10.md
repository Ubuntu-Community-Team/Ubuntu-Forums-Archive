---
title: "Error with ffmpeg since upgrade to 15.10"
date: 2015-12-26
forum: Multimedia Software
---

### Post by sir-marky on 2015-12-26
Like many of us I have been using AVCONV without major issues, however since 15.10 and the arrival of FFMPEG instead, I have errors in my scripts.

This command has been used by me for a while to rip CDs for my iPod and Fiio X5 Mk2 without error until now.

```
#!/bin/bash

cdparanoia -Bv
for f in ./*.wav; do avconv -i "$f" -acodec alac "${f%.*}.m4a"; done
eject
ls
```

replacing 'avconv' with 'ffmpeg' now brings back this error,

```
ffmpeg version 2.7.3-0ubuntu0.15.10.1 Copyright (c) 2000-2015 the FFmpeg developers
  built with gcc 5.2.1 (Ubuntu 5.2.1-22ubuntu2) 20151010
  configuration: --prefix=/usr --extra-version=0ubuntu0.15.10.1 --build-suffix=-ffmpeg --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --enable-shared --disable-stripping --enable-avresample --enable-avisynth --enable-frei0r --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopenjpeg --enable-openal --enable-libopus --enable-libpulse --enable-librtmp --enable-libschroedinger --enable-libshine --enable-libspeex --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libxvid --enable-libzvbi --enable-opengl --enable-x11grab --enable-libdc1394 --enable-libiec61883 --enable-libzmq --enable-libssh --enable-libsoxr --enable-libx264 --enable-libopencv --enable-libx265
  **WARNING: library configuration mismatch**
  avcodec     configuration: --prefix=/usr --extra-version=0ubuntu0.15.10.1 --build-suffix=-ffmpeg --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --enable-shared --disable-stripping --enable-avresample --enable-avisynth --enable-frei0r --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopenjpeg --enable-openal --enable-libopus --enable-libpulse --enable-librtmp --enable-libschroedinger --enable-libshine --enable-libspeex --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libxvid --enable-libzvbi --enable-opengl --enable-x11grab --enable-libdc1394 --enable-libiec61883 --enable-libzmq --enable-libssh --enable-libsoxr --enable-libx264 --enable-libopencv --enable-libx265 --enable-version3 --disable-doc --disable-programs --disable-avdevice --disable-avfilter --disable-avformat --disable-avresample --disable-postproc --disable-swscale --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libvo_aacenc --enable-libvo_amrwbenc
  libavutil      54. 27.100 / 54. 27.100
  libavcodec     56. 41.100 / 56. 41.100
  libavformat    56. 36.100 / 56. 36.100
  libavdevice    56.  4.100 / 56.  4.100
  libavfilter     5. 16.101 /  5. 16.101
  libavresample   2.  1.  0 /  2.  1.  0
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  2.100 /  1.  2.100
  libpostproc    53.  3.100 / 53.  3.100
Guessed Channel Layout for  Input Stream #0.0 : stereo
Input #0, wav, from './track01.cdda.wav':
  Duration: 00:02:36.20, bitrate: 1411 kb/s
    Stream #0:0: Audio: pcm_s16le ([1][0][0][0] / 0x0001), 44100 Hz, 2 channels, s16, 1411 kb/s
Output #0, ipod, to './track01.cdda.m4a':
  Metadata:
    encoder         : Lavf56.36.100
    Stream #0:0: Audio: alac (alac / 0x63616C61), 44100 Hz, stereo, s16p, 128 kb/s
    Metadata:
      encoder         : Lavc56.41.100 alac
Stream mapping:
  Stream #0:0 -> #0:0 (pcm_s16le (native) -> alac (native))
Press [q] to stop, [?] for help
size=   16226kB time=00:02:36.22 bitrate= 850.9kbits/s    
video:0kB audio:16219kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 0.046357%

```

I am uncertain how to resolve this 'WARNING: library configuration mismatch' error.

Checking other sites suggests I have installed ffmpeg on an early version of ubuntu where avconv was the default, but this wasn't the case here.

Can anyone suggest a resolution for me?

---

### Post by mc4man on 2015-12-26
Same as I told you elsewhere, it's not an error, just a warning & of no consequence. It comes from having the ffmpeg extra packages installed.
If you want the no nothing warning gone then replace libavcodec-ffmpeg-extra56 with libavcodec-ffmpeg56

---

### Post by andrew.46 on 2015-12-26
A little aside of your query: your script does not catch meta tags which would be useful at least be useful for your iPod? I am not familiar with the Fiio X5 Mk2 but perhaps this device has a similar need...

---

### Post by sir-marky on 2015-12-30
Thank you.
I used the command,

**[FONT=courier new]sudo apt-get remove libavcodec-ffmpeg-extra56[/FONT]**

libavcodec-ffmpeg56 was installed automatically to replace it by Ubuntu.

The error has now gone.
Many thanks.

---

