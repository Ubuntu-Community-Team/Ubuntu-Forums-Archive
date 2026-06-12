---
title: "Problems using WinFF"
date: 2009-09-19
forum: Multimedia Software
---

### Post by Rick Abraham on 2009-09-19
Hi guys im trying to convert a .avi file to DVD and this is what I get when I hit the convert button.

FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:20:33, gcc: 4.3.3
Input #0, avi, from '/home/ubuntu/Desktop/Terminator Salvation.avi':
  Duration: 01:46:38.90, start: 0.000000, bitrate: 1703 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 704x288 [PAR 1:1 DAR 22:9], 29.97 tbr, 29.97 tbn, 29.97 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
Unknown encoder 'mpeg2video'
Press Enter to Continue

I hit enter and nothing happens.
Can someone please tell me whats going wrong.

---

### Post by onespeedbiker on 2009-09-19
> **Rick Abraham said:**
> Hi guys im trying to convert a .avi file to DVD and this is what I get when I hit the convert button.

FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:20:33, gcc: 4.3.3
Input #0, avi, from '/home/ubuntu/Desktop/Terminator Salvation.avi':
  Duration: 01:46:38.90, start: 0.000000, bitrate: 1703 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 704x288 [PAR 1:1 DAR 22:9], 29.97 tbr, 29.97 tbn, 29.97 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
Unknown encoder 'mpeg2video'
Press Enter to Continue

I hit enter and nothing happens.
Can someone please tell me whats going wrong.

It looks like ffmpeg does not like some coding in you avi file; it found an encoder named mpeg2video that it doesn't recognise.

---

### Post by FakeOutdoorsman on 2009-09-19
You need to enable restricted encoders.  It's easy to do since it's just one package:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by Novega on 2009-09-19
hey not to hijack your thread...but what about this one?

I'm running Hardy and trying to convert .mp3 to .3g2 and i get this

```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:11:10, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Input #0, mp3, from '/home/james/Music/Iron Maiden/Dance Of Death/01 Rainmaker.mp3':
  Duration: 00:03:48.2, start: 0.000000, bitrate: 127 kb/s
  Stream #0.0: Audio: mp3, 44100 Hz, stereo, 128 kb/s
Unknown codec 'libfaac'
Press Enter to Continue
```

so I did
```
sudo apt-get install ffmpeg ubuntu-restricted-extras
```
and tried again...same thing

did ```
ffmpeg -formats |grep aac
```
and got this
```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:11:10, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
 D  aac             ADTS AAC
 DEA    aac
 D A    mpeg4aac

```

libfaac is checked off in synaptic

Any ideas on how to fix ?

---

### Post by Rick Abraham on 2009-09-20
Thanks for the help guys I have got it working. One last question tho I selected to convert my .avi file to DVD format but it converted it to a mpeg which is no good due to mpeg doesn't work with my DVD player. How do I get it to convert to .vts or .vto format which is actual DVD format ?

---

### Post by FakeOutdoorsman on 2009-09-20
> **Novega said:**
> hey not to hijack your thread...but what about this one?

I'm running Hardy and trying to convert .mp3 to .3g2 and i get this

```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:11:10, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Input #0, mp3, from '/home/james/Music/Iron Maiden/Dance Of Death/01 Rainmaker.mp3':
  Duration: 00:03:48.2, start: 0.000000, bitrate: 127 kb/s
  Stream #0.0: Audio: mp3, 44100 Hz, stereo, 128 kb/s
Unknown codec 'libfaac'
Press Enter to Continue
```

so I did
```
sudo apt-get install ffmpeg ubuntu-restricted-extras
```
and tried again...same thing

did ```
ffmpeg -formats |grep aac
```
and got this
```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:11:10, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
 D  aac             ADTS AAC
 DEA    aac
 D A    mpeg4aac

```

libfaac is checked off in synaptic

Any ideas on how to fix ?

You didn't show your FFmpeg command or which Ubuntu version you are using, so I will make a guess that you are using FFmpeg from the Medibuntu repository on Ubuntu Hardy Heron.

Medibuntu FFmpeg is kind of old, so it uses an outdated naming scheme for some encoders.  You used *-acodec libfaac*, but your version of FFmpeg requires that you use *-acodec aac* instead.  In your grepped output FFmpeg shows "DEA aac", which indicates that FFmpeg can **D**ecode and **E**ncode aac, and that aac is an **A**udio encoder.

---

### Post by Dreamlens on 2009-09-29
I was able to fix the ' unknown encoder mpeg2video' problem using Synaptic Package Manager, searching for 'libav', and enabling both of these:

libavformat-unstripped-52
libavcodec-unstripped-52

It disables the 'regular' ffmpeg libraries, but WinFF seems to work fine with the above libraries installed, though it is also easy to revert if there are other problems.

Note: I did the above after WinFF was installed.

---

### Post by paul.gevers on 2009-09-30
> **Dreamlens said:**
> 
libavformat-unstripped-52
libavcodec-unstripped-52

It disables the 'regular' ffmpeg libraries, but WinFF seems to work fine with the above libraries installed, though it is also easy to revert if there are other problems.

The unstripped libraries are binary compatible with the regular ffmpeg libraries. So no program should have a problem using either of the libraries, except that the unstripped ones have more functionality.

---

