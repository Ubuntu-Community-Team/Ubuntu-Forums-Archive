---
title: "ffmpeg scale script.. nd other questions.."
date: 2010-06-28
forum: Multimedia Software
---

### Post by rahilm on 2010-06-28
I have a lot of videos that I want to put in my mobile. However, it only supports a maximum resolution of 400x240.

Is it possible to make a script that will scale a video, preserving its aspect ratio, to match any of the boundaries. Like, if aspect ratio is 4:3, then it will scale into 320x240
Elseif aspect ratio is 16:9, it will scale it to 400x224  and so on...??

Also, i don't like putting extensions on my file. Nevertheless , when I did:
ffmpeg -i input -s 320x480 output.mp4
it shows unsupported codec.
if i don't give that mp4 extension, it says unable to determine format.
If i give .avi extension, it will begin converting.
any way to copy the codecs from the input file??

Is there a way to simply scale the video without touching it's format....?

---

### Post by FakeOutdoorsman on 2010-06-28
> **rahilm said:**
> I have a lot of videos that I want to put in my mobile. However, it only supports a maximum resolution of 400x240.

Is it possible to make a script that will scale a video, preserving its aspect ratio, to match any of the boundaries. Like, if aspect ratio is 4:3, then it will scale into 320x240
Elseif aspect ratio is 16:9, it will scale it to 400x224  and so on...??
Yes, this is possible.  Unfortunately, FFmpeg from the Ubuntu repository is too old to take advantage of some of the newer FFmpeg features such as *scale* which can accept either width or height and automatically scale the other.  I recommend compiling FFmpeg:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Basic encoding example:
```
ffmpeg -i input -acodec copy -vf 'scale=320:-1' -qscale 4 output.mp4
```
The *-1* tells the scale filter to use a height value relative to the width that will maintain the aspect ratio.

> **rahilm said:**
> Also, i don't like putting extensions on my file. Nevertheless , when I did:
ffmpeg -i input -s 320x480 output.mp4
it shows unsupported codec.
if i don't give that mp4 extension, it says unable to determine format.
If i give .avi extension, it will begin converting.
This occurs because FFmpeg from the Ubuntu repository does not have every encoder enabled by default.  Users must enable these manually and compiling FFmpeg will do just that.

When you use the mp4 extension, FFmpeg wants to use a disabled encoder (probably *libfaac *specifically in your case), but since it is not enabled you receive an error.  FFmpeg guesses the output format based on your file name extension, so if you prefer not to use an extension you will have to tell FFmpeg what to use with the *-f* option, such as *-f mp4*.

> **rahilm said:**
> Is there a way to simply scale the video without touching it's format....?
You can not resize a video without re-encoding, but you can copy the audio as shown in the encoding example.

---

### Post by rahilm on 2010-06-29
I followed instructions from here: [http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)
installed from medibuntu repository
because i didn't want to wait for compile and all..
when i entered your encoding example it gave the output:
```
ffmpeg: unrecognized option '-vf'
```
I have a big hunch that this option is for mencoder...
any similar option for ffmpeg

---

### Post by FakeOutdoorsman on 2010-06-29
> **rahilm said:**
> I followed instructions from here: [http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)
installed from medibuntu repository
because i didn't want to wait for compile and all..
when i entered your encoding example it gave the output:
```
ffmpeg: unrecognized option '-vf'
```
I have a big hunch that this option is for mencoder...
any similar option for ffmpeg

Medibuntu's FFmpeg is currently too old to use *-vf*.  You must compile FFmpeg to be able to use this option.

---

### Post by rahilm on 2010-06-29
> **FakeOutdoorsman said:**
> Medibuntu's FFmpeg is currently too old to use *-vf*.  You must compile FFmpeg to be able to use this option.
THanks. It works.
Is there a script or a pragram that will extract the width and height of a video and/or the aspect ratio?

I am thinking of making a script out of this. Like, if aspect ratio is 16:9 then convert to 320x240 etc...

And a final question...
how do i know how much time is left?? or how much has the conversion progressed??
All it shows is the current frame.. which can be useful if there is any command to know the total number of frames..
or is is written in the ffmpeg output?? i tried searching and making meaning out of things.. it shows kb/s, fps, tbr, tbc and tbn

---

### Post by FakeOutdoorsman on 2010-06-30
> **rahilm said:**
> THanks. It works.
Is there a script or a pragram that will extract the width and height of a video and/or the aspect ratio?
This should give you the width of a video:
```
ffprobe -show_streams foo.mkv 2>/dev/null | grep "width=" | cut -d'=' -f2
```
or the height:
```
ffprobe -show_streams foo.mkv 2>/dev/null | grep "height=" | cut -d'=' -f2
```
There is probably a better or nicer way of doing this, but it worked with the one video I tested.

> **rahilm said:**
> how do i know how much time is left?? or how much has the conversion progressed??
I've seen others ask this, and attempt to create a progress bar or something, but I don't know myself.  You'll have to search around.  A Google Site Search of the [ffmpeg-user mailing list archive](http://lists.mplayerhq.hu/pipermail/ffmpeg-user/) would be a good place to start.

> **rahilm said:**
> All it shows is the current frame.. which can be useful if there is any command to know the total number of frames.
You can multiply duration by frame rate to roughly find the total frames.

---

### Post by FakeOutdoorsman on 2010-07-01
You may be interested in this:

[FINALLY: A Bash Progress Indicator for ffmpeg that WORKS](http://www.prupert.co.uk/2010/05/11/finally-a-bash-progress-indicator-for-ffmpeg-that-works/)

Looks interesting. I haven't tried it myself yet, but it's written by forum member [prupert](http://ubuntuforums.org/member.php?u=312245) who also created the [x264-ffmpeg-up-to-date](http://code.google.com/p/x264-ffmpeg-up-to-date/) scripts.

---

### Post by rahilm on 2010-07-02
I followed instructions:
[http://howto-pages.org/ffmpeg/](http://howto-pages.org/ffmpeg/)
to strip portions of a video.. but i get an error..
is this expected??
```

ffmpeg -i Suraj\ hua\ maddham -ss 00:44:00 -t 00:26:00 output.mp4

FFmpeg version SVN-r23894, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jun 30 2010 07:31:26 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.19. 0 / 50.19. 0
  libavcodec    52.78. 0 / 52.78. 0
  libavformat   52.71. 0 / 52.71. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.20. 1 /  1.20. 1
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 1 codec frame rate differs from container frame rate: 59.94 (2997/50) -> 29.97 (30000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Suraj hua maddham':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: isomavc1mp42
  Duration: 00:06:18.67, start: 0.000000, bitrate: 2148 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16, 125 kb/s
    Stream #0.1(und): Video: h264, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 2019 kb/s, 29.97 fps, 29.97 tbr, 30k tbn, 59.94 tbc
Output #0, mp4, to 'output.mp4':
  Metadata:
    encoder         : Lavf52.71.0
    Stream #0.0(und): Video: mpeg4, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], q=2-31, 200 kb/s, 30k tbn, 29.97 tbc
    Stream #0.1(und): Audio: libfaac, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding
[buffer @ 0xa3fe4f0] Buffering several frames is not supported. Please consume all available frames before adding a new one.
frame=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 Lsize=       0kB time=10000000000.00 bitrate=   0.0kbits/s    
video:0kB audio:0kB global headers:0kB muxing overhead 444.680851%
Received signal 2: terminating.

```

The line
Buffering several frames is not supported. Please consume all available  frames before adding a new one.
appears in bold red.

---

### Post by FakeOutdoorsman on 2010-07-02
I've never encountered that message before.  Does FFmpeg still create a working output?  Do you get that message if you move the *-ss* option before *-i* as in:
```
ffmpeg -ss 00:44:00 -i Suraj\ hua\ maddham -t 00:26:00 output.mp4
```

---

### Post by rahilm on 2010-07-03
oops!! i did a highly qualified mistake... it is supposed to be 44 seconds and 26 seconds onwards..
so it should be
```
ffmpeg -i Suraj\ hua\ maddham -ss 00:00:44 -t 00:00:26 output.mp4
```Nevertheless... the output does not change..
the same error..

ffmpeg shows the the same line filled with 0s over and over again and all it creates is a 1.6kb file...
however,

```
ffmpeg -ss 00:00:44 -i Suraj\ hua\ maddham -t 00:00:26 output.mp4
```This works like a charm...

but wait... the audio lags by 1-2 seconds when i play the video. do i need to change the format??
This happens only with high quality videos, this one for example, is a youtube video of 720p quality.

---

### Post by FakeOutdoorsman on 2010-07-05
> **rahilm said:**
> This happens only with high quality videos, this one for example, is a youtube video of 720p quality.

Is there a particular YouTube video that this occurs on?  I can attempt to duplicate this behavior.

---

### Post by rahilm on 2010-07-07
[Discalaimer.. the word 'video' in this post means specifically videos downloaded from youtube as i don't have any other kind of video file]

> **FakeOutdoorsman said:**
> Is there a particular YouTube video that this occurs on?  I can attempt to duplicate this behavior.
[http://www.youtube.com/watch?v=eHZn85RsrCE](http://www.youtube.com/watch?v=eHZn85RsrCE)
that's the video. you'll have to select 720p in quality settings..

ok. i did a little testing with formats..here is the result.
```

ffmpeg -i input -ss *** -t *** output
```a command in this format will create the error mentioned before. but what i didn't tell was that this error happens everytime. With every video. The difference is that with low quality video, it starts converting from the second line and i get  a perfect output with audio fine tuned. But with hd videos, the process goes on forever (as told before) and I get a 1.6kb file.

```
ffmpeg -ss *** -i input -t *** output
```no error but audio lags.. on ALL videos..







UPDATE: It seems if I wait for some time, the video converts here is the output
```

fmpeg -i Suraj\ hua\ maddham -ss 46 -t 60 outputt.mp4
FFmpeg version SVN-r23894, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jun 30 2010 07:31:26 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.19. 0 / 50.19. 0
  libavcodec    52.78. 0 / 52.78. 0
  libavformat   52.71. 0 / 52.71. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.20. 1 /  1.20. 1
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 1 codec frame rate differs from container frame rate: 59.94 (2997/50) -> 29.97 (30000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Suraj hua maddham':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: isomavc1mp42
  Duration: 00:06:18.67, start: 0.000000, bitrate: 2148 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16, 125 kb/s
    Stream #0.1(und): Video: h264, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 2019 kb/s, 29.97 fps, 29.97 tbr, 30k tbn, 59.94 tbc
Output #0, mp4, to 'outputt.mp4':
  Metadata:
    encoder         : Lavf52.71.0
    Stream #0.0(und): Video: mpeg4, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], q=2-31, 200 kb/s, 30k tbn, 29.97 tbc
    Stream #0.1(und): Audio: libfaac, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding
[buffer @ 0xa7c64f0] Buffering several frames is not supported. Please consume all available frames before adding a new one.
frame=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe=    0 fps=  0 q=0.0 size=       0kB time=10000000000.00 bitrate=   0.0kbitframe= 1798 fps= 31 q=31.0 Lsize=    6994kB time=59.93 bitrate= 956.0kbits/s    
video:6490kB audio:468kB global headers:0kB muxing overhead 0.516860%

```So there is no error. video plays perfectly.. just a problem with my patience..


MARKING THREAD AS SOLVED.. until i get into another problem.. (I am trying to make a video now with multiple subtitles encoded.. mkv sounds good but i doubt ffmpeg can do that)

---

### Post by aaronLund on 2010-10-02
Was there any progress made on finding out why your audio was lagging?

I'm having the same problem.

---

