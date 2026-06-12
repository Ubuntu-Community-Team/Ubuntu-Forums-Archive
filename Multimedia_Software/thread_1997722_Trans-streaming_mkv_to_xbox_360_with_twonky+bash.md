---
title: "Trans-streaming mkv to xbox 360 with twonky+bash"
date: 2012-06-05
forum: Multimedia Software
---

### Post by klikevil on 2012-06-05
Okay so I recently discovered the magic of twonky for linux to stream media to xbox however to my dismay I discovered that transcoding isn't 100% effective and in general media needs to be converted for the xbox to even recognize it.  I found this quite frustrating and decided to make a little work around for this for those of you that don't feel like converting thousands of matorska files.  

	Please be gentle, as I'm not sure how effective this is and I'm still on my first test with it.  So far it seems to be working okay, but someone might be able to get some use out of this post and or improve on it or suggest a better method.  

First off you're going to need to set twonky to refresh every minute rather than as content is added.

Once this has been done run this script in the directory of the media you plan on converting
```
#!/bin/bash
# This started out from humble beginings, as you can see below
# for i in {1..1} ; do ffmpeg -i `ls | head -$i | tail -1` -map 0:1 -vcodec libx264 -acodec ac3 $1.wmv ; done
echo "PLEASE NOTE THAT YOU MAY HAVE TO ADJUST THIS BASED OFF THE VIDEO FILE YOU ARE WATCHING"

# Without further adue, the one liner to output an entire directory to a single file.  Preserved in its original glory in the comment below.

# for i in {1..1} ; do ffmpeg -i `ls | head -$i | tail -1` -r 23.98 -b:v 1358k  -map 0:0 -map 0:1 -vcodec wmv2 -acodec wmav2 $1.wmv ; done

count=`ls|wc -l` ; for (( i=1; i<$count; i++ )) ; do ffmpeg -i `ls | head -$i | tail -1` -r 23.98 -b:v 1358k  -map 0:0 -map 0:1 -vcodec wmv2 -acodec wmav2 $1.wmv ; sleep 60 ; done

```

This will convert one video at a time starting from the top and put them all in the same file.  You may adjust the sleep to your liking for better timing.  This isn't exactly playing a mkv, but it saves time on the conversion process and allows you to just keep repeating the same file for a new video :D .  Open to suggestions for a better way.  You will also have to manually over write with this script, so it's a good idea to have a laptop handy to proceed.  Below is an output of what it will look like in action

```
root@epiphany /media/jessica_NAS/Downloads/YuYu Hakusho # streamtofile wmv1
PLEASE NOTE THAT YOU MAY HAVE TO ADJUST THIS BASED OFF THE VIDEO FILE YOU ARE WATCHING
ffmpeg version 0.11 Copyright (c) 2000-2012 the FFmpeg developers
  built on Jun  5 2012 11:22:40 with gcc 4.3.3
  configuration: --enable-gpl --enable-libx264 --extra-cflags=-I/usr/local/include --extra-ldflags='-L/usr/local/lib -L/usr/lib/' --disable-pthreads --enable-static --enable-shared --enable-libxvid --enable-libmp3lame --enable-libvpx
  libavutil      51. 54.100 / 51. 54.100
  libavcodec     54. 23.100 / 54. 23.100
  libavformat    54.  6.100 / 54.  6.100
  libavdevice    54.  0.100 / 54.  0.100
  libavfilter     2. 77.100 /  2. 77.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0. 15.100 /  0. 15.100
  libpostproc    52.  0.100 / 52.  0.100
[mpeg4 @ 0x845e4a0] Warning: not compiled with thread support, using thread emulation
[aac @ 0x845eb60] Warning: not compiled with thread support, using thread emulation
[aac @ 0x845f260] Warning: not compiled with thread support, using thread emulation
[mpeg4 @ 0x845e4a0] Invalid and inefficient vfw-avi packed B frames detected
Input #0, matroska,webm, from '(B-A)Yu_Yu_Hakusho_-_01_(A424940E).mkv':
  Metadata:
    creation_time   : 2004-08-31 23:10:36
  Duration: 00:23:44.00, start: 0.000000, bitrate: 1358 kb/s
    Stream #0:0(eng): Video: mpeg4 (Advanced Simple Profile) (XVID / 0x44495658), yuv420p, 640x480 [SAR 255:191 DAR 340:191], SAR 1:1 DAR 4:3, 23.98 fps, 23.98 tbr, 1k tbn, 23.98 tbc (default)
    Metadata:
      title           : Video Stream
    Stream #0:1(eng): Audio: aac, 44100 Hz, stereo, s16 (default)
    Metadata:
      title           : English Audio
    Stream #0:2(jpn): Audio: aac, 44100 Hz, stereo, s16
    Metadata:
      title           : Japanese Audio
    Stream #0:3(eng): Subtitle: text (default)
    Metadata:
      title           : English Subtitles
File 'wmv1.wmv' already exists. Overwrite ? [y/N] y
w:640 h:480 pixfmt:yuv420p tb:1/1000 sar:1/1 sws_param:flags=2
[buffersink @ 0x8492440] No opaque field provided
[wmv2 @ 0x84913e0] Warning: not compiled with thread support, using thread emulation
[wmav2 @ 0x8491ba0] Warning: not compiled with thread support, using thread emulation
[mpeg4 @ 0x845e4a0] Warning: not compiled with thread support, using thread emulation
[aac @ 0x845eb60] Warning: not compiled with thread support, using thread emulation
Output #0, asf, to 'wmv1.wmv':
  Metadata:
    creation_time   : 2004-08-31 23:10:36
    WM/EncodingSettings: Lavf54.6.100
    Stream #0:0(eng): Video: wmv2 (WMV2 / 0x32564D57), yuv420p, 640x480 [SAR 1:1 DAR 4:3], q=2-31, 1358 kb/s, 1k tbn, 23.98 tbc (default)
    Metadata:
      title           : Video Stream
    Stream #0:1(eng): Audio: wmav2 (a[1][0][0] / 0x0161), 44100 Hz, stereo, s16, 127 kb/s (default)
    Metadata:
      title           : English Audio
Stream mapping:
  Stream #0:0 -> #0:0 (mpeg4 -> wmv2)
  Stream #0:1 -> #0:1 (aac -> wmav2)
Press [q] to stop, [?] for help
[mpeg4 @ 0x845e4a0] Invalid and inefficient vfw-avi packed B frames detected
frame=34149 fps= 97 q=2.0 Lsize=  263847kB time=00:23:44.06 bitrate=1517.8kbits/s dup=7 drop=0    
video:235651kB audio:22248kB global headers:0kB muxing overhead 2.306358%
ffmpeg version 0.11 Copyright (c) 2000-2012 the FFmpeg developers
  built on Jun  5 2012 11:22:40 with gcc 4.3.3
  configuration: --enable-gpl --enable-libx264 --extra-cflags=-I/usr/local/include --extra-ldflags='-L/usr/local/lib -L/usr/lib/' --disable-pthreads --enable-static --enable-shared --enable-libxvid --enable-libmp3lame --enable-libvpx
  libavutil      51. 54.100 / 51. 54.100
  libavcodec     54. 23.100 / 54. 23.100
  libavformat    54.  6.100 / 54.  6.100
  libavdevice    54.  0.100 / 54.  0.100
  libavfilter     2. 77.100 /  2. 77.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0. 15.100 /  0. 15.100
  libpostproc    52.  0.100 / 52.  0.100
[mpeg4 @ 0x9ef64a0] Warning: not compiled with thread support, using thread emulation
[aac @ 0x9ef6ae0] Warning: not compiled with thread support, using thread emulation
[aac @ 0x9ef71c0] Warning: not compiled with thread support, using thread emulation
[mpeg4 @ 0x9ef64a0] Invalid and inefficient vfw-avi packed B frames detected
Input #0, matroska,webm, from '(B-A)Yu_Yu_Hakusho_-_02_(826945F3).mkv':
  Metadata:
    creation_time   : 2004-11-01 05:09:10
  Duration: 00:23:44.46, start: 0.000000, bitrate: 1354 kb/s
    Stream #0:0: Video: mpeg4 (Advanced Simple Profile) (XVID / 0x44495658), yuv420p, 640x480 [SAR 255:191 DAR 340:191], SAR 1:1 DAR 4:3, 23.98 fps, 23.98 tbr, 1k tbn, 23.98 tbc (default)
    Metadata:
      title           : Video Stream
    Stream #0:1(eng): Audio: aac, 48000 Hz, stereo, s16 (default)
    Metadata:
      title           : English Audio
    Stream #0:2(jpn): Audio: aac, 48000 Hz, stereo, s16
    Metadata:
      title           : Japanese Audio
    Stream #0:3(eng): Subtitle: text (default)
    Metadata:
      title           : English Subtitles
File 'wmv1.wmv' already exists. Overwrite ? [y/N]
```

enjoy

---

