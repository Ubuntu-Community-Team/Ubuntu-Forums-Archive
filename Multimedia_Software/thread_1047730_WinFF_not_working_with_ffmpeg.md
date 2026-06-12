---
title: "WinFF not working with ffmpeg?"
date: 2009-01-22
forum: Multimedia Software
---

### Post by SCTPenguin on 2009-01-22
Not sure if this is the right section of the forum (I apologize if it's not), but I have a problem with winff and converting files. It keeps giving me this when I try to convert, and seeing that I've only had ubuntu a week, I have no idea what the hell it all means.

I've spent a few hours googling, and I can't figure it out. Any help would be much appreciated. Thanks.

```
FFmpeg version UNKNOWN-svn15824+3:0.svn20081115-1ubuntu1+unstripped1~ppa1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn15824+3:0.svn20081115-1ubuntu1+unstripped1~ppa1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-libmp3lame --enable-libfaac --enable-libfaad --enable-libdirac --disable-encoder=libschroedinger --disable-decoder=libdirac --enable-gpl --enable-libxvid --enable-gpl --enable-libx264 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52. 3. 0 / 52. 3. 0
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 1. 0 /  0. 1. 0
  libswscale     0. 6. 1 /  0. 6. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Dec 30 2008 05:50:58, gcc: 4.3.2
[theora @ 0x88de2e0]7 bits left in packet 82
Input #0, ogg, from '/home/collin/Desktop/Avant_Wtf.ogv':
  Duration: 00:00:26.86, start: 0.000000, bitrate: 2838 kb/s
    Stream #0.0: Invalid Codec type -1
    Stream #0.1: Video: theora, yuv420p, 1440x896, 15.00 tb(r)
    Stream #0.2: Audio: vorbis, 48000 Hz, mono, s16, 239 kb/s
Unable to parse option value "trell": undefined constant or missing (
Unable to parse option value "trell": undefined constant or missing (
Unable to parse option value "trell": undefined constant or missing (
Unable to parse option value "trell": undefined constant or missing (
/usr/bin/ffmpeg: unrecognized option '-flags'
Press Enter to Continue  

```

---

### Post by FakeOutdoorsman on 2009-01-22
What WinFF preset are you using?

---

### Post by SCTPenguin on 2009-01-22
> **FakeOutdoorsman said:**
> What WinFF preset are you using?

a Youtube preset I downloaded. Youtube 640x360 Avg (16:9)

---

### Post by FakeOutdoorsman on 2009-01-22
Can you paste the preset settings?  Or show me where you got it and I can give you a version that will work.

---

### Post by SCTPenguin on 2009-01-22
> **FakeOutdoorsman said:**
> Can you paste the preset settings?  Or show me where you got it and I can give you a version that will work.

Heres the presets. [http://www.mediafire.com/?y2yilyzdzy2](http://www.mediafire.com/?y2yilyzdzy2)

---

### Post by FakeOutdoorsman on 2009-01-22
This should work and replaces YTXviDWS.wff:
```
<?xml version="1.0"?>
<presets>
  <YTXviDWS>
    <label>Youtube 640x360 Avg (16:9)</label>
    <params>-r 29.97 -vcodec libxvid -s 640x360 -aspect 16:9 -maxrate 2000k -b 1500k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -flags +4mv+aic -trellis 1 -cmp 2 -subcmp 2 -g 300 -acodec libfaac -ar 48000 -ab 192k -ac 2</params>
    <extension>mp4</extension>
    <category>Youtube</category>
  </YTXviDWS>
</presets>
```
or you could use ffmpeg itself:
```
ffmpeg -i input.avi -vcodec libxvid -s 640x360 -aspect 16:9 -maxrate 2000k -b 1500k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -flags +4mv+aic -trellis 1 -cmp 2 -subcmp 2 -g 300 -acodec libfaac -ar 48000 -ab 192k -ac 2 output.mp4
```

---

### Post by SCTPenguin on 2009-01-22
I love you. Thanks man, I appreciate it.

---

### Post by paul.gevers on 2009-01-24
Depending on where you got your version of winff it includes the presets file that you should replace your presets.xml file with (Your/usr/share/doc/winff/README.Debian should tell you). Replace the file in you ~/.winff/presets.xml with the /usr/share/winff/presets-libavcodec52-v2.xml (if you have it) renaming the latter to presets.xml.

You can get the correct presets file for your version of ffmpeg here: [http://winff.googlecode.com/files/presets-r15824-v2.tar.gz](http://winff.googlecode.com/files/presets-r15824-v2.tar.gz)

---

### Post by CiaoCiao on 2009-02-15
Awesome...Thanks...Update presets fixed the same problem I was encountering.

---

### Post by motin on 2009-03-08
> **paul.gevers said:**
> Depending on where you got your version of winff it includes the presets file that you should replace your presets.xml file with (Your/usr/share/doc/winff/README.Debian should tell you). Replace the file in you ~/.winff/presets.xml with the /usr/share/winff/presets-libavcodec52-v2.xml (if you have it) renaming the latter to presets.xml.

You can get the correct presets file for your version of ffmpeg here: [http://winff.googlecode.com/files/presets-r15824-v2.tar.gz](http://winff.googlecode.com/files/presets-r15824-v2.tar.gz)

Big Thanks! It turned out that all that was needed was:
```
cp /usr/share/winff/presets-libavcodec52-v2.xml ~/.winff/presets.xml
```

No download required. 

My ffmpeg version info btw:
```
FFmpeg version SVN-r17862, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.21. 0 / 52.21. 0
  libavformat   52.31. 1 / 52.31. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  7 2009 19:03:26, gcc: 4.3.2

```

---

