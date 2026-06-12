---
title: "Encoding video for Samsung Tocco video playback"
date: 2009-08-05
forum: Multimedia Software
---

### Post by Lord Stig on 2009-08-05
Hi all.
I have a lovely new Samsung Tocco and want to convert videos to watch on it.
The software bundled with it will convert to the correct format but I can't get it to run under Wine (nothing appears after the splash screen) and I expect that transcoding in Ubuntu 8.10 is best with Linux apps.
Also, the Samsung software and some other freeware ones on my old XP machine have given it blue screen of death and now it won't boot at all (not even a BIOS beep so maybe it just died of old age).

Avidemux is the tool I have used briefly for editing and re-encoding and there are some auto options in the menu (e.g. Auto iPod, PSP, PSP H264) but none of these will play. I have read the Tocco needs the res to be 320x240 so I specify this, and am told it will play H263 and H264 standards and/or MPEG4. I have tried converting a short video using the following (with all other settings left at their defaults as I don't know what I'm messing with) but always get "unsupported file type":
Auto iPOD (320x240), xvid 4, format as MP4.
MPEG4 AVX x264, format as MP4.
iPod 320x240 then changed encoder to MPEG-4 ASP (LAVC), MP4 format. Produced a file I thought would play (what I know of settings and file size looked ok) but it didn't. File properties as they appear in Nautilus: 
Lavf51.12.1 320x240 MPEG-4 25fps, MPEG-4 AAC audio stereo 48KHz bit rate n/a

I know x263 and x264 are opensource versions of H263 and H264; could this be the problem? But for me it could be anything.

Appreciate your help immensely but with any reply please spell everything out for me! I'm not familiar with the command line so if I could get the right settings for Avidemux or be pointed in the direction of an easy to use program I'd very much appreciate it. My source isn't a DVD but an XVid file of some kind.

Cheers.

---

### Post by benerivo on 2009-08-05
I only know how it could be done as a command line, but it isn't too complex. Make sure the ffmpeg package is installed and then try running this command...```
ffmpeg -i '/home/thomas/video.avi' -s qvga -qscale 1 -ab 128k -ac 1 '/home/thomas/mobile-video.mp4
```where -s qvga is the resolution of 320*240, -qscale 1 is the best video quality setting, -ab 128k is the audio bitrate (otherwise defaults to 64 which is a bit low for me), and -ac 1 sets the audio to mono as the phone will proabaly only have one speaker.

---

### Post by Lord Stig on 2009-08-08
Thanks for your reply. I get the following.

[INDENT]cp@cp-desktop:~$ ffmpeg -i '/media/Maxtor 250GB USB2/TV/Doctor Who 2008 - Series 4/S4E10 Midnight.avi' -s qvga -qscale 1 -ab 128k -ac 1 '/home/s4e10.mp4> ffmpeg -i '/media/Maxtor 250GB USB2/TV/Doctor Who 2008 - Series 4/S4E10 Midnight.avi' -s qvga -qscale 1 -ab 128k -ac 1 '/home/s4e10.mp4
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
Input #0, avi, from '/media/Maxtor 250GB USB2/TV/Doctor Who 2008 - Series 4/S4E10 Midnight.avi':
  Duration: 00:43:47.2, start: 0.000000, bitrate: 1111 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x352 [PAR 1:1 DAR 20:11], 25.00 tb(r)
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, 112 kb/s
Unable to find a suitable output format for '/home/s4e10.mp4
ffmpeg -i /media/Maxtor'
cp@cp-desktop:~$ [/INDENT]

---

### Post by benerivo on 2009-08-08
Reading through all of [this thread]("http://ubuntuforums.org/showthread.php?t=1144106"), it seems that you may have to add the multiverse repository which contains the correct ffmpeg libraries to enable mp4 support. To do this, just go to Software Sources in the menu, and enable the extra repoistories.

---

### Post by FakeOutdoorsman on 2009-08-09
> **Lord Stig said:**
> Thanks for your reply. I get the following.
\cp@cp-desktop:~$ ffmpeg -i '/media/Maxtor 250GB USB2/TV/Doctor Who 2008 - Series 4/S4E10 Midnight.avi' -s qvga -qscale 1 -ab 128k -ac 1 '/home/s4e10.mp4> ffmpeg -i '/media/Maxtor 250GB USB2/TV/Doctor Who 2008 - Series 4/S4E10 Midnight.avi' -s qvga -qscale 1 -ab 128k -ac 1 '/home/s4e10.mp4

...

Unable to find a suitable output format for '/home/s4e10.mp4
ffmpeg -i /media/Maxtor'


You got this error because your FFmpeg syntax was not correct.  You entered two FFmpeg commands on one line and FFmpeg assumed that your output file was named */home/s4e10.mp4 ffmpeg -i /media/Maxtor*.

---

