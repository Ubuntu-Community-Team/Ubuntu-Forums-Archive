---
title: "FFmpeg"
date: 2008-11-08
forum: Multimedia Software
---

### Post by warrior24 on 2008-11-08
Hello all I am trying to transfer my VHS to DVD and when I try to record using this command all I get is a poor quality video.

 ffmpeg -t hh:mm:ss -i /dev/video0 -acodec copy -vcodec copy moviename.mpg

haupauge 350
AMD 2600+
1gbram
500gb disk space

---

### Post by warrior24 on 2008-11-09
any one this is so frustrating](*,)

---

### Post by FakeOutdoorsman on 2008-11-09
Once reason your video quality is low is because ffmpeg will use a default bitrate of 200k if you don't specify one.  FFmpeg has a few "target" options that will set the bitrate, codecs, and other format settings automatically.  Try:
```
ffmpeg -i input -target pal-dvd output.mpg
```

---

### Post by warrior24 on 2008-11-10
adrian@adrian-desktop:~$ ffmpeg -i input -target pal-dvd output.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
input: I/O error occured
Usually that means that input file is truncated and/or corrupted.
adrian@adrian-desktop:~$ 


Thanks in advance I feel like I am slowly getting somewhere. don't know if the attached file will be of any help. its my ffmpegformant.txt

---

### Post by FakeOutdoorsman on 2008-11-10
> **warrior24 said:**
> input: I/O error occured
You're getting that error because you used "input" instead of defining what your input really is.  In my previous post, I just used "input" as an example.

---

### Post by warrior24 on 2008-11-10
adrian@adrian-desktop:~$ ffmpeg -i /dev/video0 -target pal-dvd output.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
/dev/video0: Unknown format
adrian@adrian-desktop:~$

---

### Post by Cracauer on 2008-11-10
This is my biggest annoyance about Linux video tools. They aren't smart enough to, when using one file as input and one as output, use the same parameters for both. What gives? Lame doesn't downgrade CD quality input to to 8 bit 10 KHz either.

The best way to find good parameters is to inspect files that you think are of acceptable quality. 

I use `mplayer -v filename.blah`.

It gives you:
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  8500.0 kbps (1062.5 kbyte/s)
AUDIO: 48000 Hz, 2 ch, s16le, 224.0 kbit/14.58% (ratio: 28000->192000)

---

### Post by warrior24 on 2008-11-16
I got it recording with your help but I get pixelated video.

 ffmpeg -i /dev/video0 -target ntsc-dvd test1.mpg

---

### Post by Cresho on 2008-11-16
[http://ubuntuforums.org/showthread.php?p=6182889#post6182889](http://ubuntuforums.org/showthread.php?p=6182889#post6182889)

---

### Post by warrior24 on 2008-11-23
I still cant get it to work as from what I understand tv time does not work with hauupauge 350

---

### Post by warrior24 on 2008-11-24
here is what I get when I type in this command. ](*,)

adrian@adrian-desktop:~$ mencoder -tv norm=NTSC:driver=v4l2:width=720:height=480:input=2:fps=29.97 tv:// -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf pp=lb/ha/va/dr,hqdn3d,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1500:vrc_maxrate=8000:vbitrate=7000:keyint=15:acodec=mp2:abitrate=192:aspect=4/3 -o capture.mpg 
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm)  (Family: 6, Model: 10, Stepping: 0)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Hauppauge WinTV PVR-350
 Tuner cap: STEREO LANG1 LANG2
 Tuner rxs: STEREO
 Capabilites:  video capture  video output  VBI capture device  VBI output  tuner  audio  read/write
 supported norms: 0 = PAL-BGH; 1 = PAL-DK; 2 = PAL-I; 3 = PAL-M; 4 = PAL-N; 5 = PAL-Nc; 6 = SECAM-BGH; 7 = SECAM-DK; 8 = SECAM-L; 9 = SECAM-L'; 10 = NTSC-M; 11 = NTSC-J; 12 = NTSC-K;
 inputs: 0 = Tuner 1; 1 = S-Video 1; 2 = Composite 1; 3 = S-Video 2; 4 = Composite 2; 5 = Composite 3;
 Current input: 1
 Current format: unknown (0x4745504d)
v4l2: current audio mode is : STEREO
tv.c: norm_from_string(NTSC): Bogus norm parameter, setting default.
Audio block size too low, setting to 16384!
v4l2: ioctl request buffers failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.
Segmentation fault
adrian@adrian-desktop:~$ 
adrian@adrian-desktop:~$

---

