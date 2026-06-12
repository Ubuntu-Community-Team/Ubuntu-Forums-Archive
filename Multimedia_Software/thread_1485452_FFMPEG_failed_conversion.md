---
title: "FFMPEG failed conversion"
date: 2010-05-16
forum: Multimedia Software
---

### Post by domzz on 2010-05-16
I'm using the newest FFMPEG and when I try to convert, I get this error:

```
Started on 2010-05-16 04:25:57 - 2010 May 16

Checking File ....
File : /home/tvstarcraft/public_html/files/conversion_queue/12739767060d705.mp4
File Exists : Yes

Preparing file...
format : mov,mp4,m4a,3gp,3g2,mj2
duration : 57.98
size : 4024511
bitrate : 542
video_width : 480
video_height : 360
video_wh_ratio : 1.3333333333333
video_codec : h264
video_rate : 29.97585374267
video_bitrate : 448
video_color : yuv420p
audio_codec : aac
audio_bitrate : 91
audio_rate : 44100
audio_channels : stereo
path : /home/tvstarcraft/public_html/files/conversion_queue/12739767060d705.mp4

Converting Video
Conversion Command : /usr/local/bin/ffmpeg -i /home/tvstarcraft/public_html/files/conversion_queue/12739767060d705.mp4 -f flv -vcodec libx264 -vpre normal -r 30 -b 512000 -s 400x300 -aspect 1.3333333333333 -padcolor 000000 -padtop 0 -padbottom 0 -padleft 0 -padright 0 -acodec libfaac -ab 128000 -ar 32000 -map_meta_data /home/tvstarcraft/public_html/files/videos/12739767060d705.flv:/home/tvstarcraft/public_html/files/conversion_queue/12739767060d705.mp4 /home/tvstarcraft/public_html/files/videos/12739767060d705.flv 2> /home/tvstarcraft/public_html/files/temp/127397675779a22.tmp


Conversion Details

FFmpeg version SVN-r23143, Copyright (c) 2000-2010 the FFmpeg developers
built on May 16 2010 04:20:38 with gcc 4.4.3
configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
libavutil 50.15. 2 / 50.15. 2
libavcodec 52.67. 0 / 52.67. 0
libavformat 52.62. 0 / 52.62. 0
libavdevice 52. 2. 0 / 52. 2. 0
libavfilter 1.20. 0 / 1.20. 0
libswscale 0.10. 0 / 0.10. 0
libpostproc 51. 2. 0 / 51. 2. 0

Seems stream 1 codec frame rate differs from container frame rate: 59.94 (2997/50) -> 29.97 (30000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/tvstarcraft/public_html/files/conversion_queue/12739767060d705.mp4':
Metadata:
major_brand : mp42
minor_version : 0
compatible_brands: isomavc1mp42
Duration: 00:00:57.99, start: 0.000000, bitrate: 555 kb/s
Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16, 93 kb/s
Stream #0.1(und): Video: h264, yuv420p, 480x360 [PAR 1:1 DAR 4:3], 459 kb/s, 29.97 fps, 29.97 tbr, 30k tbn, 59.94 tbc
Please use vf=pad
ERROR: No such file or directory - /home/tvstarcraft/public_html/files/videos/12739767060d705.flv
ERROR: /usr/lib/ruby/1.8/flvtool2/base.rb:259:in `initialize'
ERROR: /usr/lib/ruby/1.8/flvtool2/base.rb:259:in `open'
ERROR: /usr/lib/ruby/1.8/flvtool2/base.rb:259:in `open_stream'
ERROR: /usr/lib/ruby/1.8/flvtool2/base.rb:238:in `process_files'
ERROR: /usr/lib/ruby/1.8/flvtool2/base.rb:225:in `each'
ERROR: /usr/lib/ruby/1.8/flvtool2/base.rb:225:in `process_files'
ERROR: /usr/lib/ruby/1.8/flvtool2/base.rb:44:in `execute!'
ERROR: /usr/lib/ruby/1.8/flvtool2.rb:168:in `execute!'
ERROR: /usr/lib/ruby/1.8/flvtool2.rb:228
ERROR: /usr/bin/flvtool2:2:in `require'
ERROR: /usr/bin/flvtool2:2
Failed to stat file /home/tvstarcraft/public_html/files/videos/12739767060d705.flv!
Failed to stat file /home/tvstarcraft/public_html/files/videos/12739767060d705.flv!


Unknown file details - Unable to get output video details using FFMPEG 


Time Took : 0.0585 seconds

conversion_status : failed
```

---

### Post by andrew.46 on 2010-05-17
Hi domzz,

Could you try the same conversion using the commandline FFmpeg only?

Andrew

---

### Post by jcalcote on 2010-06-28
> **domzz said:**
> I'm using the newest FFMPEG and when I try to convert, I get this error:

```
Started on 2010-05-16 04:25:57 - 2010 May 16

Checking File ....
File : /home/tvstarcraft/public_html/files/conversion_queue/12739767060d705.mp4
File Exists : Yes

Preparing file...
format : mov,mp4,m4a,3gp,3g2,mj2
duration : 57.98
size : 4024511
bitrate : 542
video_width : 480
video_height : 360
video_wh_ratio : 1.3333333333333
video_codec : h264
video_rate : 29.97585374267
video_bitrate : 448
video_color : yuv420p
audio_codec : aac
audio_bitrate : 91
audio_rate : 44100
audio_channels : stereo
path : /home/tvstarcraft/public_html/files/conversion_queue/12739767060d705.mp4

Converting Video
Conversion Command : /usr/local/bin/ffmpeg -i /home/tvstarcraft/public_html/files/conversion_queue/12739767060d705.mp4 -f flv -vcodec libx264 -vpre normal -r 30 -b 512000 -s 400x300 -aspect 1.3333333333333 -padcolor 000000 -padtop 0 -padbottom 0 -padleft 0 -padright 0 -acodec libfaac -ab 128000 -ar 32000 -map_meta_data /home/tvstarcraft/public_html/files/videos/12739767060d705.flv:/home/tvstarcraft/public_html/files/conversion_queue/12739767060d705.mp4 /home/tvstarcraft/public_html/files/videos/12739767060d705.flv 2> /home/tvstarcraft/public_html/files/temp/127397675779a22.tmp


Conversion Details

FFmpeg version SVN-r23143, Copyright (c) 2000-2010 the FFmpeg developers
built on May 16 2010 04:20:38 with gcc 4.4.3
configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
libavutil 50.15. 2 / 50.15. 2
libavcodec 52.67. 0 / 52.67. 0
libavformat 52.62. 0 / 52.62. 0
libavdevice 52. 2. 0 / 52. 2. 0
libavfilter 1.20. 0 / 1.20. 0
libswscale 0.10. 0 / 0.10. 0
libpostproc 51. 2. 0 / 51. 2. 0

Seems stream 1 codec frame rate differs from container frame rate: 59.94 (2997/50) -> 29.97 (30000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/tvstarcraft/public_html/files/conversion_queue/12739767060d705.mp4':
Metadata:
major_brand : mp42
minor_version : 0
compatible_brands: isomavc1mp42
Duration: 00:00:57.99, start: 0.000000, bitrate: 555 kb/s
Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16, 93 kb/s
Stream #0.1(und): Video: h264, yuv420p, 480x360 [PAR 1:1 DAR 4:3], 459 kb/s, 29.97 fps, 29.97 tbr, 30k tbn, 59.94 tbc
Please use vf=pad
...

```

Here's your problem - late versions of ffmpeg changed command line options from padright/padleft, etc to -vf "pad=w:x:y:z,crop=...". 

Unfortunately, they haven't updated the ffmpeg docs yet, and they've broken backward compatibility with a LOT of applications. 

John

---

