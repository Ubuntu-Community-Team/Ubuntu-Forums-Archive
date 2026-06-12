---
title: "ffmpeg / avc / mp4 -  Video not working on HTC G1"
date: 2010-08-31
forum: Multimedia Software
---

### Post by _chafouin_ on 2010-08-31
Hello,

I'm having trouble to find the right ffmpeg options to encode a video that can be read on a htc G1 cell phone.
I have used several codecs and formats but none is working.

I have followed these instruction to install ffmpeg and x264
[http://ubuntuforums.org/showpost.php?p=9114176&postcount=967](http://ubuntuforums.org/showpost.php?p=9114176&postcount=967)

Here is my ffmpeg config :
```

FFmpeg version SVN-r24953, Copyright (c) 2000-2010 the FFmpeg developers
  built on Aug 27 2010 22:44:01 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.24. 0 / 50.24. 0
  libavcore      0. 6. 0 /  0. 6. 0
  libavcodec    52.87. 0 / 52.87. 0
  libavformat   52.78. 3 / 52.78. 3
  libavdevice   52. 2. 1 / 52. 2. 1
  libavfilter    1.38. 1 /  1.38. 1
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0

```and here is a sample line, i have tried :
```

ffmpeg -i input.avi -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre slow -crf 22 -threads 0 output.mp4

```but the generated video can not be read on the G1

I managed to create a video that is working, but on Windows :confused::confused::confused:
Here are the informations provided by ffmpeg about this file
```
Seems stream 0 codec frame rate differs from container frame rate: 59.94 (2997/50) -> 29.97 (2997/100)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '2010-07-19_22-57-23.MP4':
  Metadata:
    major_brand     : mp42
    minor_version   : 1
    compatible_brands: isomiso2avc1mp41mp423gp5
    title           : 2010-07-19_22-57-23.MP4
    comment         : 22:57:44
  Duration: 00:00:19.58, start: 0.000000, bitrate: 133 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 480x272 [PAR 34:45 DAR 4:3], 131 kb/s, PAR 181:240 DAR 181:136, 29.97 fps, 29.97 tbr, 2997 tbn, 59.94 tbc
    Stream #0.1(und): Data: mp4s / 0x7334706D, 0 kb/s
    Stream #0.2(und): Data: mp4s / 0x7334706D, 0 kb/s

```What would be the command line to generate such a file with ffmpeg ???

Thanks for your help.

---

### Post by FakeOutdoorsman on 2010-08-31
A slight modification to your command may allow it to play on that device.  This is a guess on my part because I don't own this phone (additions in [color=#FF0000]red[/color]):
```
ffmpeg -i input.avi -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre slow \
[color=#FF0000]-vpre ipod320 -vf scale=320:-1[/color] -crf 22 -threads 0 output.mp4
```

---

### Post by _chafouin_ on 2010-08-31
Thanks FakeOutdoorsman,
 
I have tried your modifications and unfortunatly it is not working.
I still get the message "Unable to read video file".

I was wondering if the issue is not due to the "major brand" of the file.
Which is "isom" in the file generated with ffmpeg and "mp42" in the file that is working.

Is it possible to force this kind of option in ffmpeg ???

Thanks

---

### Post by FakeOutdoorsman on 2010-08-31
You can try the *-vtag* option, but I don't have much experience with this option:
```
ffmpeg -i output.mp4 -vtag foo -vcodec copy -acodec copy newoutput.mp4
```

---

