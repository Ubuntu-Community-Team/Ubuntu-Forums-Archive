---
title: "Help Converting and Burning a DVD"
date: 2010-11-24
forum: Multimedia Software
---

### Post by derricklongley on 2010-11-24
I need something that will convert and then burn a DVD. I have tried almost all of the options on Ubuntu including Devede, K3B, Avidemux, Qauthor, Tovid, Transmageddon, DVDstyler and probably more. None will convert to a NTSC format without trying to create a DVD menu which seems to be the problem involved in playback except for Transmageddon, but it fails to provide the bup and ifo files to go with the video files to get K3B to burn it. I'm able to make DVD's that work on computers, but I want DVD's that will play in my DVD player. Any programs other than the ones I named that can do the conversion without creating a DVD menu and create all the files needed to get K3B to burn it? If needed, I'm converting from AVI. Also, I will take all suggestions, thanks

---

### Post by derricklongley on 2010-11-24
I'm trying DVDstyler again because I found out it allows you to delete the menus that it comes with. I will still consider any other options too.

---

### Post by derricklongley on 2010-11-24
Nope, did avi to iso in DVDstyler then burned the iso with K3B and it works fine in the computer, but won't play in DVD player, get disc error doen't have playback feature.

---

### Post by mitchroberts on 2010-11-24
> **derricklongley said:**
> I need something that will convert and then burn a DVD. I have tried almost all of the options on Ubuntu including Devede, K3B, Avidemux, Qauthor, Tovid, Transmageddon, DVDstyler and probably more. None will convert to a NTSC format without trying to create a DVD menu which seems to be the problem involved in playback except for Transmageddon, but it fails to provide the bup and ifo files to go with the video files to get K3B to burn it. I'm able to make DVD's that work on computers, but I want DVD's that will play in my DVD player. Any programs other than the ones I named that can do the conversion without creating a DVD menu and create all the files needed to get K3B to burn it? If needed, I'm converting from AVI. Also, I will take all suggestions, thanks

devede will convert and burn a dvd in ntsc format but for me it's just slow so i downloaded tovid the one in synaptic doesn't work so i installed from svn now it works great.

---

### Post by derricklongley on 2010-11-25
Yes, Devede did burn a DVD, but the DVD will not play in a DVD player that all my DVD's used to and still play in. I think its more than a menu issue because I was able to use DVDstyler and I didn't create a menu, but the DVD still didn't play. What else could be the problem? Are you talking about running tovid completely from the command line because I can't seem to get it to run from there, but I'm working on it to see if works.

---

### Post by derricklongley on 2010-11-27
any ideas?

---

### Post by ron999 on 2010-11-27
> **derricklongley said:**
> any ideas?
Hi
Look at this thread, post #14 here:- [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1626970]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1626970")

---

### Post by derricklongley on 2010-11-28
I have switched to trying to use the terminal

I have been trying to follow directions like below, but I have oly been able to complete the first instruction. Can someone throughly explain step two because I have seen instructions with more stuff to do listed, but both ways produced this error

 
DVDAuthor::dvdauthor, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>




#1 Convert the file to MPEG-2.
Code:
ffmpeg -i filename.avi -target ntsc-dvd foo.mpg
(Creates a file named foo.mpg)

#2 Build the file structure.
Code:
dvdauthor -o DVD/ -t foo.mpg && dvdauthor -o DVD/ -T
(Creates a folder named DVD)

#3 Make an iso.
Code:
mkisofs -dvd-video -v -o DVD.iso DVD
(Creates a file named DVD.iso)
EDIT
If the mkisofs command doesn't work, use genisoimage instead, like this:-
Code:
genisoimage -dvd-video -v -o DVD.iso DVD

---

### Post by ron999 on 2010-11-29
Hi
Paste in the command:-
```
ffmpeg -i foo.mpg
```

Then copy and paste **_all_** the output here.

Just like this:-

> ron@ubuntu:~$ ffmpeg -i foo.mpg
FFmpeg version SVN-r25751, Copyright (c) 2000-2010 the FFmpeg developers
  built on Nov 14 2010 13:43:35 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab --disable-encoder=vorbis
  libavutil     50.33. 0 / 50.33. 0
  libavcore      0.12. 1 /  0.12. 1
  libavcodec    52.94. 4 / 52.94. 4
  libavformat   52.84. 0 / 52.84. 0
  libavdevice   52. 2. 2 / 52. 2. 2
  libavfilter    1.62. 0 /  1.62. 0
  libswscale     0.12. 0 /  0.12. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[mpeg @ 0x9c874c0] max_analyze_duration reached
Input #0, mpeg, from 'foo.mpg':
  Duration: 00:03:00.00, start: 1.000000, bitrate: 2797 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 1:1 DAR 3:2], 9000 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, s16, 448 kb/s
At least one output file must be specified
ron@ubuntu:~$

---

### Post by derricklongley on 2010-11-29
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
foo.mpg: no such file or directory

---

### Post by ron999 on 2010-11-30
> **derricklongley said:**
> FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
[COLOR="Red"]foo.mpg: no such file or directory[/COLOR]

Hi
Looks like you need to run the first command:-
```
ffmpeg -i [COLOR="Red"]filename[/COLOR].avi -target ntsc-dvd foo.mpg
```
Then when it's finished use:-
```
ffmpeg -i foo.mpg
```
Then post the output again.

---

### Post by runeh76 on 2010-11-30
Not superman in this thing, but have u tryed mandvd ?

Cheers Runeh

---

### Post by derricklongley on 2010-12-01
Tried mandvd, but I have recently found out that the DVD player only plays NTSC, so I will give it another shot and get back to you. Still it would be good to learn how to burn a DVD with this other process too.


FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
filename.avi: no such file or directory



FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
foo.mpg: no such file or directory

---

### Post by derricklongley on 2010-12-01
Mandvd did work, so it was not knowing the settings to make dvd's play on my dvd player.

---

### Post by runeh76 on 2010-12-01
> **derricklongley said:**
> Mandvd did work, so it was not knowing the settings to make dvd's play on my dvd player.

WOW cool !! It was just (look that way)..
Havent use it myself.  



:popcorn:

---

