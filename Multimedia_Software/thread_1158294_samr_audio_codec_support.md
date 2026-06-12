---
title: "samr audio codec support"
date: 2009-05-13
forum: Multimedia Software
---

### Post by sydbata on 2009-05-13
Hi All, 

I am having problems with converting a 3gp file to flv using ffmpeg. Here is the error which I receive: 

user@ubuntu:~/Desktop$ ffmpeg -i VIDEO_050.3gp -f flv -acodec libmp3lame  -ar 22050 -ab 64k -ac 1 video.flv
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'VIDEO_050.3gp':
  Duration: 00:01:11.8, start: 0.000000, bitrate: 375 kb/s
    Stream #0.0(eng): Video: mpeg4, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 30.00 tb(r)
    **Stream #0.1(eng): Audio: samr / 0x726D6173, 8000 Hz, mono**
Output #0, flv, to 'video.flv':
    Stream #0.0(eng): Video: flv, yuv420p, 320x240 [PAR 1:1 DAR 4:3], q=2-31, 200 kb/s, 30.00 tb(c)
    Stream #0.1(eng): Audio: libmp3lame, 22050 Hz, mono, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
**[COLOR=black]Unsupported codec (id=73728) for input stream #0.1[/COLOR]**

It seems that my ffmpeg doesn't support samr audio codec. Can you please let me know how I can enable that? 

Thanks a lot in advance!
Cheers!

---

### Post by logos34 on 2009-05-13
I think you need to uninstall ffmpeg and recompile from source with amr enabled:

Here's mine:
> 
$ ffmpeg -formats | grep 3gp
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 [COLOR="Red"]--enable-amr_nb --enable-amr_wb[/COLOR] --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:11:10, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
  E 3g2             3gp2 format
  E 3gp             3gp format
 DE amr             3gpp amr file format
 D  mov,mp4,m4a,3gp,3g2,mj2 QuickTime/MPEG4/Motion JPEG 2000 format

---

### Post by FakeOutdoorsman on 2009-05-13
These instructions will help you compile FFmpeg with AMR support:
[Re: How to play AMR audio files](http://ubuntuforums.org/showpost.php?p=6320667&postcount=9)

---

### Post by sydbata on 2009-06-21
Hey guys, 

Thanks a lot for your help! That really worked! Now I am able to convert the files correctly.

Cheers!

---

