---
title: "dvc-100, mencoder - errors"
date: 2013-08-01
forum: Multimedia Software
---

### Post by squakie on 2013-08-01
I have ubuntu 13.04 and a Pinnacle DVC-100 video capture device that I am trying to capture VHS tapes to disk with.  I know absolutely nothing about any of this.  I found a blog entry with the following command in it (I changed the output file name but left the suffix the same).  As you can see, I get errors.  As per the blog, I tried this with mplyer with all of the output stuff removed.  The results were mixed - I get what appears to be great screen clarity and capture, however no sound and no color - only black and white.

If anyone has done this successfully with the DVC-100 (this is my 3rd different device type to try to do this) PLEASE post what you did.

If anyone can find the problem in what I did or need more information, please let me know.
```
dave@dwezbox1:~$ mencoder tv://  -tv  driver=v4l2:device=/dev/video0:input=0:norm=ntsc:alsa:audiorate=48000:adevice=copy:forceaudio:immediatemode=0 -of mpeg -mpegopts format=dvd -ofps 30000/1001 -vf scale=720:480,harddup -ovc lavc -oac lavc -lavcopts acodec=ac3:abitrate=192:keyint=25:vcodec=mpeg2video:vbitrate=4000:aspect=4/3 -o ~/testmovie.m4v
MEncoder svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team

WARNING: OUTPUT FILE FORMAT IS _MPEG_. See -of help.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Pinnacle Dazzle DVC 90/100/101/
 Capabilities:  video capture  audio  read/write  streaming
 supported norms: 0 = NTSC; 1 = NTSC-M; 2 = NTSC-M-JP; 3 = NTSC-M-KR; 4 = NTSC-443; 5 = PAL; 6 = PAL-BG; 7 = PAL-H; 8 = PAL-I; 9 = PAL-DK; 10 = PAL-M; 11 = PAL-N; 12 = PAL-Nc; 13 = PAL-60; 14 = SECAM; 15 = SECAM-B; 16 = SECAM-G; 17 = SECAM-H; 18 = SECAM-DK; 19 = SECAM-L; 20 = SECAM-Lc;
 inputs: 0 = Composite1; 1 = S-Video;
 Current input: 0
 Current format: YUYV
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
Selected input hasn't got a tuner!
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Error opening audio: No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Error opening audio: No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Error opening audio: No such file or directory
v4l2: 0 frames successfully processed, 0 frames dropped.
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...
dave@dwezbox1:~$ 

```

---

