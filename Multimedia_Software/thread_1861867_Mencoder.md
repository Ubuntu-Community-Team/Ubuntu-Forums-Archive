---
title: "Mencoder"
date: 2011-10-16
forum: Multimedia Software
---

### Post by shantiq on 2011-10-16
Everytime i cut h264 video with Mencoder i get this message


>  mencoder  -ss 00:023:07  -endpos 00:5:09 -oac pcm -ovc copy later.mp4 -o ff1.mp4  && mencoder  -ss 00:58:01  -endpos 00:06:00 -oac pcm -ovc copy later.mp4 -o ff2.mp4   && mencoder  -oac copy -ovc copy -o  final2.mp4  ff1.mp4 ff2.mp4 
MEncoder 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
success: format: 0  data: 0x0 - 0x4f6b16dd
libavformat file format detected.
**[h264 @ 0xece350]brainfart cropping not supported, this could look slightly wrong ...**
[aac @ 0xecebe0]Transition from an ONLY_LONG or LONG_STOP to an EIGHT_SHORT sequence detected. If you heard an audible artifact, please submit the sample to the FFmpeg developers.
[lavf] stream 0: video (h264), -vid 0




and it does look a bit wrong not a lot mind but at the start it tears for a second or too then goes back to normal


ANY idea how to rectify this?.


see [**here**]("http://www.youtube.com/watch?v=ADwqzX65uHI")   and [**here **]("http://www.youtube.com/watch?v=RpzUiwjDCDs")

---

### Post by SeijiSensei on 2011-10-17
I'm puzzled as to why you get this error:

> WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.

when you specify .mp4 as the container in every command.  Did you run "mencoder -of help" as suggested?  

Googling for that message shows a lot of postings some of which are about creating files in the MP4 container.  It looks like you need to be using -of lavf with some relevant -lavfdopts specified.

---

### Post by shantiq on 2011-10-17
ok sensei thanx for reply

the original file is here

> mediainfo later.mp4
General
Complete name                    : later.mp4
Format                           : MPEG-4
Format profile                   : Base Media
Codec ID                         : isom
File size                        : 1.24 GiB
Duration                         : 1h 4mn
Overall bit rate                 : 2 766 Kbps
Movie name                       : Later... with Jools Holland
Performer                        : Later... with Jools Holland
Genre                            : Music
Encoded date                     : 2011-10-14T23:55:00+01:00
Tagged date                      : UTC 2011-10-15 11:04:36
[B][COLOR="Red"]Writing application              : Lavf52.64.2
[/COLOR][/B]Cover                            : Yes
Comment                          : With Peter Gabriel, The Horrors, Noah & the Whale, Lana Del Rey, and Ghostpoet.
tvnn                             : BBC HD
desc                             : With Peter Gabriel, The Horrors, Noah & the Whale, Lana Del Rey, and Ghostpoet.
tvsh                             : Later... with Jools Holland
tven                             : b0161733
rtng                             : 2
stik                             : 10
tvsn                             : 39
tves                             : 4

Video
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L4.1
Format settings, CABAC           : Yes
Format settings, ReFrames        : 6 frames
Codec ID                         : avc1
Codec ID/Info                    : Advanced Video Coding
Duration                         : 1h 4mn
Bit rate mode                    : Variable
Bit rate                         : 2 666 Kbps
Width                            : 1 280 pixels
Height                           : 720 pixels
Display aspect ratio             : 16/9
Frame rate                       : 25.000 fps
Original frame rate              : 25.000 fps
Standard                         : PAL
Resolution                       : 24 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.116
Stream size                      : 1.20 GiB (96%)
Encoded date                     : UTC 1970-01-01 00:00:00
Tagged date                      : UTC 1970-01-01 00:00:00

Audio
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format version                   : Version 4
Format profile                   : LC
Format settings, SBR             : No
Codec ID                         : 40
Duration                         : 1h 4mn
Bit rate mode                    : Variable
Bit rate                         : 96.0 Kbps
Channel(s)                       : 2 channels
Channel positions                : L R
Sampling rate                    : 24.0 KHz
Resolution                       : 16 bits
Stream size                      : 43.5 MiB (3%)
Encoded date                     : UTC 1970-01-01 00:00:00
Tagged date                      : UTC 1970-01-01 00:00:00




so you probably are on the right track here



this kind of [**options **]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-libavcodec.html#menc-feat-enc-libavcodec-video-codecs")  ```
-ovc lavc -lavcopts vcodec=





``` sorry not clear about how to go forward; anyone got ideas about specifics :KS

---

### Post by FakeOutdoorsman on 2011-10-17
Your times are formatted oddly, but MEncoder probably gets it: 00:023:07 00:5:09. Does FFmpeg work as expected?
```
ffmpeg -i input.mp4 -vcodec copy -acodec copy -ss 00:23:07.00 -t 00:05:09.00 output.mp4
```

---

### Post by shantiq on 2011-10-17
> interesting sideway thinking Fake one and here is the answer. Sadly since i know you are a fan of ffmpeg [as really i am]; but in recent times i have been using mencoder more for video cutting but still always ffmpeg for audio conversions

I have had quite a few problems with cutting vid with ffmpeg


But anyway i digress

In this instance same old same old  

> ffmpeg -i later.mp4 -vcodec copy -acodec copy -ss 00:23:07.00 -t 00:05:09.00 output.mp4
shantiq@shan:~/Videos$ ffmpeg -i later.mp4 -vcodec copy -acodec copy -ss 00:01:02.00 -t 00:05:09.00 output0.mp4
FFmpeg version 0.6.2-4:0.6.2-1ubuntu1.1, Copyright (c) 2000-2010 the Libav developers
  built on Sep 16 2011 17:00:39 with gcc 4.5.2
  configuration: --extra-version=4:0.6.2-1ubuntu1.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavcodec  configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[COLOR="Red"][h264 @ 0x1c35ad0]brainfart cropping not supported, this could look slightly wrong ...
[aac @ 0x1c36350]Transition from an ONLY_LONG or LONG_STOP to an EIGHT_SHORT sequence detected. If you heard an audible artifact, please submit the sample to the FFmpeg developers.[/COLOR]
    Last message repeated 1 times
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'later.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    encoder         : Lavf52.64.2
    network         : BBC HD



original file was obtained with get-iplayer [a BBC-iplayer program] maybe there is a kink in the file
I often have problems with those but not always



as regards  > Your times are formatted oddly i have always seen it that way with mencoder nothing beyond seconds :)

---

