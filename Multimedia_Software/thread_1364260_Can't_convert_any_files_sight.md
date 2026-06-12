---
title: "Can't convert any files *sight*"
date: 2009-12-25
forum: Multimedia Software
---

### Post by iTheBadGuy on 2009-12-25
Ok, so I've read like 15 topics about this, but no luck. I must be doing something wrong, I just don't know what.

I got a .mov and want to convert it into a .mp4 or .avi. I've tried with ffmpeg but when i type:
```
ffmpeg -i /home/ithebadguy/source-video.mov /home/ithebadguy/output-video.mp4
```I get this:
```
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 100.00 (100/1) -> 13.01 (3731993/286847)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/ithebadguy/Desktop/House.MOV':
  Duration: 00:01:11.71, start: 0.000000, bitrate: 1837 kb/s
    Stream #0.0(eng): Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 13.01 tbr, 13.01 tbn, 100 tbc
    Stream #0.1(eng): Audio: pcm_mulaw, 16000 Hz, mono, s16, 128 kb/s
Output #0, mp4, to '/home/ithebadguy/Desktop/Test.mp4':
    Stream #0.0(eng): Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], q=2-31, 200 kb/s, 90k tbn, 13.01 tbc
    Stream #0.1(eng): Audio: 0x0000, 16000 Hz, mono, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg4 @ 0x97f5280]timebase not supported by mpeg 4 standard
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
```I get the same for .avi.

I also tried this command:
```
ffmpeg -i /home/ithebadguy/Desktop/source-video.MOV -s 480x320 -vcodec mpeg4 -acodec libfaac -ac 1 -ar 16000 -r 13 -ab 32000 -aspect 3:2 /home/ithebadguy/Desktop/output-video.mp4
```I get this:
```
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 100.00 (100/1) -> 13.01 (3731993/286847)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/ithebadguy/Desktop/House.MOV':
  Duration: 00:01:11.71, start: 0.000000, bitrate: 1837 kb/s
    Stream #0.0(eng): Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 13.01 tbr, 13.01 tbn, 100 tbc
    Stream #0.1(eng): Audio: pcm_mulaw, 16000 Hz, mono, s16, 128 kb/s
Unknown encoder 'libfaac'
```Question: Why is it so damn hard to convert a file?! -_-'. Someone just give me step-by-step instructions on how to convert this file from .MOV to .MP4.. please.

---

### Post by HappyFeet on 2009-12-25
Try [Handbrake]("http://handbrake.fr/downloads.php"). Works good for me. 2 clicks and you are done.

---

### Post by FakeOutdoorsman on 2009-12-25
> **iTheBadGuy said:**
> Ok, so I've read like 15 topics about this, but no luck. I must be doing something wrong, I just don't know what.

Your commands were probably fine, but FFmpeg from the Karmic repository is a little hobbled.  In previous Ubuntu versions you could simply enable restricted formats such as MP3 and AAC by installing a single package (libavcodec-unstripped-52 or libavcodec-extra-52), but in Karmic this extra package does not include AAC audio which is a popular format.

You have a few options: try a different audio format, install *libavcodec-extra-52* from Medibuntu, or compile FFmpeg.

For a different audio format first make sure you have *libavcodec-extra-52* installed:
```
sudo apt-get install libavcodec-extra-52
```
Now the command.  Because your file already contains video (mpeg4 format) that works fine in a MP4 container you can just copy and paste the video stream from your input file to your output file with *-vcodec copy*.
```
ffmpeg -i input.mov -vcodec copy -acodec libmp3lame output.mp4
```

To use the more capaple Medibuntu version of *libavcodec-extra-52*, see option C in:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Now the command:
```
ffmpeg -i input.mov -vcodec copy output.mp4
```

If you want to re-encode or change various options such as frame size (-s 320x240 for example), use the Medibuntu package or compile FFmpeg and:
```
ffmpeg -i input.mov -vcodec libx264 -vpre hq -crf 24 -threads 0 output.mp4
```
This will encode your video to the H.264 format using the *libx264* encoder.  This is the encoding method I usually use.

To compile FFmpeg yourself see option A in the above link.  I recommend this option if you do a good amount of video converting or if your file proves to be troublesome.  You'll get the newest version of FFmpeg if you compile and it comes with a good number of bugfixes and quality enhancements that are absent in FFmpeg from the repository.

---

### Post by iTheBadGuy on 2010-01-02
Thanks FakeOutdoorsman, that helped a lot! :D

---

