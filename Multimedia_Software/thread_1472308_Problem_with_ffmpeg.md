---
title: "Problem with ffmpeg"
date: 2010-05-04
forum: Multimedia Software
---

### Post by bg11 on 2010-05-04
I'm trying to make the resolution of a video smaller.  So I tried using ffmpeg (version 5:0.5.1+svn20100427-0.0)

```
> ffmpeg -i project.avi -s 320x240 small.avi
```

This resulted in the following error:

```

FFmpeg version UNKNOWN, Copyright (c) 2000-2010 the FFmpeg developers                                   
  built on Apr 27 2010 16:47:40 with gcc 4.4.3                                                          
  configuration: --enable-libdc1394 --prefix=/usr --extra-cflags='-Wall -g ' --cc='ccache cc' --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libtheora --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libspeex --enable-nonfree --disable-stripping --enable-avfilter --enable-libdirac --enable-avfilter-lavf --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --enable-version3 --enable-libopenjpeg --disable-altivec --disable-armv5te --disable-armv6 --disable-vis                                                                                                              
  WARNING: library configuration mismatch                                                                                          
  libavutil   configuration: --enable-libdc1394 --prefix=/usr --extra-cflags='-Wall -g ' --cc='ccache cc' --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libtheora --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libspeex --enable-nonfree --disable-stripping --enable-avfilter --enable-libdirac --enable-avfilter-lavf --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --enable-version3 --enable-libopenjpeg --cpu=i686 --disable-static --disable-ffprobe --disable-ffmpeg --disable-ffplay --shlibdir=/usr/lib/i686/cmov                                                      
  libavcodec  configuration: --enable-libdc1394 --prefix=/usr --extra-cflags='-Wall -g ' --cc='ccache cc' --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libtheora --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libspeex --enable-nonfree --disable-stripping --enable-avfilter --enable-libdirac --enable-avfilter-lavf --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --enable-version3 --enable-libopenjpeg --cpu=i686 --disable-static --disable-ffprobe --disable-ffmpeg --disable-ffplay --shlibdir=/usr/lib/i686/cmov                                                      
  libavformat configuration: --enable-libdc1394 --prefix=/usr --extra-cflags='-Wall -g ' --cc='ccache cc' --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libtheora --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libspeex --enable-nonfree --disable-stripping --enable-avfilter --enable-libdirac --enable-avfilter-lavf --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --enable-version3 --enable-libopenjpeg --cpu=i686 --disable-static --disable-ffprobe --disable-ffmpeg --disable-ffplay --shlibdir=/usr/lib/i686/cmov                                                      
  libavdevice configuration: --enable-libdc1394 --prefix=/usr --extra-cflags='-Wall -g ' --cc='ccache cc' --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libtheora --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libspeex --enable-nonfree --disable-stripping --enable-avfilter --enable-libdirac --enable-avfilter-lavf --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --enable-version3 --enable-libopenjpeg --cpu=i686 --disable-static --disable-ffprobe --disable-ffmpeg --disable-ffplay --shlibdir=/usr/lib/i686/cmov                                                      
  libavfilter configuration: --enable-libdc1394 --prefix=/usr --extra-cflags='-Wall -g ' --cc='ccache cc' --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libtheora --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libspeex --enable-nonfree --disable-stripping --enable-avfilter --enable-libdirac --enable-avfilter-lavf --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --enable-version3 --enable-libopenjpeg --cpu=i686 --disable-static --disable-ffprobe --disable-ffmpeg --disable-ffplay --shlibdir=/usr/lib/i686/cmov                                                      
  libswscale  configuration: --enable-libdc1394 --prefix=/usr --extra-cflags='-Wall -g ' --cc='ccache cc' --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libtheora --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libspeex --enable-nonfree --disable-stripping --enable-avfilter --enable-libdirac --enable-avfilter-lavf --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --enable-version3 --enable-libopenjpeg --cpu=i686 --disable-static --disable-ffprobe --disable-ffmpeg --disable-ffplay --shlibdir=/usr/lib/i686/cmov                                                      
  libpostproc configuration: --enable-libdc1394 --prefix=/usr --extra-cflags='-Wall -g ' --cc='ccache cc' --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libtheora --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libspeex --enable-nonfree --disable-stripping --enable-avfilter --enable-libdirac --enable-avfilter-lavf --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --enable-version3 --enable-libopenjpeg --cpu=i686 --disable-static --disable-ffprobe --disable-ffmpeg --disable-ffplay --shlibdir=/usr/lib/i686/cmov
  libavutil     50.14. 0 / 50.14. 0
  libavcodec    52.66. 0 / 52.66. 0
  libavformat   52.61. 0 / 52.61. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, avi, from 'project.avi':
  Metadata:
    ISFT            : AVI-Mux GUI 1.17.8.3, Feb 16 201019:42:50
    JUNK            :
  Duration: 01:52:53.48, start: 0.000000, bitrate: 1105 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 672x288 [PAR 1:1 DAR 7:3], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, 5.1, s16, 192 kb/s
    Metadata:
      strn            : VTS_02_1 T80 3_2ch 448Kbps DELAY 0ms_new
[mp2 @ 0x8d56d60]encoding 6 channel(s) is not allowed in mp2
Output #0, avi, to 'small.avi':
    Stream #0.0: Video: mpeg4, yuv420p, 320x240 [PAR 7:4 DAR 7:3], q=2-31, 200 kb/s, 90k tbn, 25 tbc
    Stream #0.1: Audio: mp2, 48000 Hz, 5.1, s16, 64 kb/s
    Metadata:
      strn            : VTS_02_1 T80 3_2ch 448Kbps DELAY 0ms_new
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
**Error while opening encoder for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height**

```

The error isn't very helpful, it's very difficult to see what actually went wrong.

Here's the output from ffmpeg -version:

```

  libavutil     50.14. 0 / 50.14. 0
  libavcodec    52.66. 0 / 52.66. 0
  libavformat   52.61. 0 / 52.61. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
FFmpeg UNKNOWN
libavutil     50.14. 0 / 50.14. 0
libavcodec    52.66. 0 / 52.66. 0
libavformat   52.61. 0 / 52.61. 0
libavdevice   52. 2. 0 / 52. 2. 0
libavfilter    1.19. 0 /  1.19. 0
libswscale     0.10. 0 /  0.10. 0
libpostproc   51. 2. 0 / 51. 2. 0

```

---

### Post by xzero1 on 2010-05-04
Could it be this line **[mp2 @ 0x8d56d60]encoding 6 channel(s) is not allowed in mp2**?

---

### Post by LuridCinema on 2010-05-04
Sometimes adding parameters such as frame rate, sound settings and even  -sameq will work when the basic settings do not work. AND I have found that sometimes only the basic settings work when fancier settings give errors.

I have had to sometimes re-encode the clip using ffmpeg from simply INPUT.avi to OUTPUT.avi and THEN encode to the desired output. Funny, but it works for me... It just may be that ffmpeg does not like your input file's information, but when ffmpeg encodes it , THEN it will allow you to encode again..

I have some files that are in .WMV format and I wanted to use ffmpeg to take a 2 minute clip and only output 20secs as an .MPG file, I get errors. I found that I had to simply have ffmpeg encode the files from WMV to MPG,  THEN have ffmpeg cut it into 20 sec clips.. it worked !

---

### Post by FakeOutdoorsman on 2010-05-04
> **bg11 said:**
> I'm trying to make the resolution of a video smaller.  So I tried using ffmpeg (version 5:0.5.1+svn20100427-0.0)

```
configuration: --enable-libdc1394 --prefix=/usr --extra-cflags='-Wall -g ' --cc='ccache cc' --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libtheora --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libspeex --enable-nonfree --disable-stripping --enable-avfilter --enable-libdirac --enable-avfilter-lavf --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --enable-version3 --enable-libopenjpeg --disable-altivec --disable-armv5te --disable-armv6 --disable-vis
...
WARNING: library configuration mismatch
```

This is the messiest FFmpeg configure that I've encountered.  Where did you get this FFmpeg package?  Google says Debian Multimedia.  You generally should not install packages from Debian Multimedia on an Ubuntu system.  What a mess.

I recommend uninstalling any Debian Multimedia packages and following:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Then, as xzero1 mentioned, you need to reduce the number of output channels (using *-ac 2*) or just copy the audio from the input to the output:
```
ffmpeg -i project.avi -acodec copy -qscale 4 -s 320x240 small.avi
```
I added *-qscale 4*, otherwise FFmpeg will use a default of *-b 200k* which can look bad.

---

