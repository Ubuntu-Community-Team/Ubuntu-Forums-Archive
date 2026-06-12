---
title: "Ffmpeg and capturing video in segments...."
date: 2013-09-14
forum: Multimedia Software
---

### Post by timsdeepsky on 2013-09-14
Can ffmpeg capture raw video from /dev/video3 in 10 minute segments on the fly??....I see information on segments,,but mainly for rtsp and playlists....
I simply need to capture 24/7 video from /dev/video3 in 10 minute segments,,and have them all saved to a folder....Preferrably without missing any video in between segments....
Thanks for any direction you may offer....

These are the last updates i have been able to find on the matter....
[http://trac.ffmpeg.org/ticket/26]("http://trac.ffmpeg.org/ticket/26")
[https://trac.ffmpeg.org/ticket/1504]("https://trac.ffmpeg.org/ticket/1504")


Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-53-generic
GNOME 3.4.2
ffmpeg 7:201303030806-git-1

---

### Post by FakeOutdoorsman on 2013-09-15
You can use the [segment muxer](http://ffmpeg.org/ffmpeg-formats.html#segment_002c-stream_005fsegment_002c-ssegment):
```
ffmpeg -f v4l2 -i /dev/video3 -codec copy -map 0 -f segment -segment_time 600 space/meteors_%04d.mkv
```

Resulting in (notice the typo):
```
 $ ls -m1 space
mereors_0000.mkv
mereors_0001.mkv
mereors_0002.mkv
...

```

The output video and container formats may not be what you want. I used "-codec copy" to [stream copy](http://ffmpeg.org/ffmpeg.html#Stream-copy) instead of re-encoding and Matroska container because you gave no specifics about the output and you did not provide any details about your input device:
```
ffmpeg -f v4l2 -i /dev/video3
```
and
```
ffmpeg -f v4l2 -list_formats all -i /dev/video3
```

Also see [FFmpeg video4linux2 input device docs](http://ffmpeg.org/ffmpeg-devices.html#video4linux2_002c-v4l2).

---

### Post by timsdeepsky on 2013-09-15
Thanks for your help once again FakeOutdoorsman....
I would like to be able to capture the video on the fly from (/dev/video3) and output it as raw(-codec copy) or mp4 into the segments....If the raw segments ended up being too large,,i would fall back to outputting to mp4 to save space....

```
ffmpeg -f v4l2 -i /dev/video3
```
Outputs this....
```
tim@tim-quad-core:~$ ffmpeg -f v4l2 -i /dev/video3
ffmpeg version N-43174-gf4e29c4 Copyright (c) 2000-2013 the FFmpeg developers
  built on Sep 15 2013 12:48:28 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --prefix=/home/tim/ffmpeg_build --extra-cflags=-I/home/tim/ffmpeg_build/include --extra-ldflags=-L/home/tim/ffmpeg_build/lib --bindir=/home/tim/bin --extra-libs=-ldl --enable-gpl --enable-libass --enable-libfdk-aac --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab --enable-libfreetype
  libavutil      52. 17.102 / 52. 17.102
  libavcodec     54. 92.100 / 54. 92.100
  libavformat    54. 63.100 / 54. 63.100
  libavdevice    54.  3.103 / 54.  3.103
  libavfilter     3. 38.103 /  3. 38.103
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100
[video4linux2,v4l2 @ 0x32aa5a0] Estimating duration from bitrate, this may be inaccurate
Input #0, video4linux2,v4l2, from '/dev/video3':
  Duration: N/A, start: 34999.105470, bitrate: 147456 kb/s
    Stream #0:0: Video: rawvideo (YUY2 / 0x32595559), yuyv422, 640x480, 147456 kb/s, 30 fps, 30 tbr, 1000k tbn, 1000k tbc
At least one output file must be specified

```
```
ffmpeg -f v4l2 -list_formats all -i /dev/video3
```
Outputs this....
```
tim@tim-quad-core:~$ ffmpeg -f v4l2 -list_formats all -i /dev/video3
ffmpeg version N-43174-gf4e29c4 Copyright (c) 2000-2013 the FFmpeg developers
  built on Sep 15 2013 12:48:28 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --prefix=/home/tim/ffmpeg_build --extra-cflags=-I/home/tim/ffmpeg_build/include --extra-ldflags=-L/home/tim/ffmpeg_build/lib --bindir=/home/tim/bin --extra-libs=-ldl --enable-gpl --enable-libass --enable-libfdk-aac --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab --enable-libfreetype
  libavutil      52. 17.102 / 52. 17.102
  libavcodec     54. 92.100 / 54. 92.100
  libavformat    54. 63.100 / 54. 63.100
  libavdevice    54.  3.103 / 54.  3.103
  libavfilter     3. 38.103 /  3. 38.103
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100
[video4linux2,v4l2 @ 0x340c6a0] Raw       :   yuyv422 :     YUV 4:2:2 (YUYV) : 640x480 352x288 320x240 176x144 160x120 544x288 432x240 320x176 640x360
[video4linux2,v4l2 @ 0x340c6a0] Compressed:     mjpeg :                MJPEG : 640x480 352x288 320x240 176x144 160x120 544x288 432x240 320x176 640x360 800x480 1024x768
/dev/video3: Immediate exit requested

```

When i use this code
```
ffmpeg -f v4l2 -i /dev/video3 -codec copy -map 0 -f segment -segment_time 600 space/meteors_%04d.mkv
```
i get....
```
tim@tim-quad-core:~$ ffmpeg -f v4l2 -i /dev/video3 -codec copy -map 0 -f segment -segment_time 600 space/meteors_%04d.mkv
ffmpeg version N-43174-gf4e29c4 Copyright (c) 2000-2013 the FFmpeg developers
  built on Sep 15 2013 12:48:28 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --prefix=/home/tim/ffmpeg_build --extra-cflags=-I/home/tim/ffmpeg_build/include --extra-ldflags=-L/home/tim/ffmpeg_build/lib --bindir=/home/tim/bin --extra-libs=-ldl --enable-gpl --enable-libass --enable-libfdk-aac --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab --enable-libfreetype
  libavutil      52. 17.102 / 52. 17.102
  libavcodec     54. 92.100 / 54. 92.100
  libavformat    54. 63.100 / 54. 63.100
  libavdevice    54.  3.103 / 54.  3.103
  libavfilter     3. 38.103 /  3. 38.103
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100
[video4linux2,v4l2 @ 0x32c8100] Estimating duration from bitrate, this may be inaccurate
Input #0, video4linux2,v4l2, from '/dev/video3':
  Duration: N/A, start: 35230.835941, bitrate: 147456 kb/s
    Stream #0:0: Video: rawvideo (YUY2 / 0x32595559), yuyv422, 640x480, 147456 kb/s, 30 fps, 29.92 tbr, 1000k tbn, 1000k tbc
Output #0, segment, to 'space/meteors_%04d.mkv':
  Metadata:
    encoder         : Lavf54.63.100
    Stream #0:0: Video: rawvideo (YUY2 / 0x32595559), yuyv422, 640x480, q=2-31, 147456 kb/s, 30 fps, 90k tbn, 1000k tbc
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
Could not write header for output file #0 (incorrect codec parameters ?): No such file or directory

```

I can capture video from this cam with this code perfectly....
```
ffmpeg -f video4linux2 -s 640x480 -r ntsc -i /dev/video3 -qscale 3 test.mpeg  
```
So far i have not been able to add the segment code to any other capture code to make it work(yet)....
But i will get there eventually....I capture some of my video from ffmpeg in bash scripts like this....
```
#!/bin/bash
/usr/local/bin/ffmpeg -framerate 30/1 -f video4linux2 -video_size 640x480 -i /dev/video4 -t 03:00:00 -vf drawtext="fontfile=/usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf:text='Cline_sky_cam_west_':timecode='$(date +%H\\:%M\\:%S).00': r=30/1: x=(w-tw)/2: y=h-(1*lh): fontcolor=white: fontsize=16: box=1: boxcolor=0x00000999" -vcodec libx264 -preset slow -crf 28 -movflags faststart -acodec libfaac -aq 100 /home/tim/bin/sunset_cronkilltoo.mp4
```
and they are perfect....But i am trying to change over one of my cams to the 10 minute segments that are captured in real time and simply stored in a folder numbered in order....
I am still studying the [muxer]("http://ffmpeg.org/ffmpeg-formats.html#segment_002c-stream_005fsegment_002c-ssegment") part....

My ffmpeg version....
```
FFMPEG VERSION
ffmpeg version N-43174-gf4e29c4 Copyright (c) 2000-2013 the FFmpeg developers
  built on Sep 15 2013 12:48:28 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --prefix=/home/tim/ffmpeg_build --extra-cflags=-I/home/tim/ffmpeg_build/include --extra-ldflags=-L/home/tim/ffmpeg_build/lib --bindir=/home/tim/bin --extra-libs=-ldl --enable-gpl --enable-libass --enable-libfdk-aac --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab --enable-libfreetype
  libavutil      52. 17.102 / 52. 17.102
  libavcodec     54. 92.100 / 54. 92.100
  libavformat    54. 63.100 / 54. 63.100
  libavdevice    54.  3.103 / 54.  3.103
  libavfilter     3. 38.103 /  3. 38.103
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100

```

Thanks for any more assistance you may be able to help me with....

---

### Post by timsdeepsky on 2013-09-15
I have finally had some luck using ffmpeg and segments....
This code spits out 30 second continuous segments of video from my /dev/video3....
```
ffmpeg -f video4linux2 -input_format mjpeg -i /dev/video3 -c:v copy -map 0 -f segment -segment_time 30 space/meteors_%04d.mkv
```
Now to see if i can integrate the timecode into it....

---

### Post by FakeOutdoorsman on 2013-09-16
> ```
ffmpeg version N-43174-gf4e29c4 Copyright (c) 2000-2013 the FFmpeg developers
  built on Sep 15 2013 12:48:28 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)

```

This looks odd. It appears you compiled yesterday, but the git commit hash f4e29c4 is from 17 Feb 2013:

```
$ cd ffmpeg
$ git log f4e29c4
commit f4e29c408ceae9f34b427fbe3d8b6706478c36f9
Author: Paul B Mahol <onemda@gmail.com>
Date:   Sun Feb 17 21:05:33 2013 +0000

    lavfi/noise: switch to AVLFG noise generator
    
    Signed-off-by: Paul B Mahol <onemda@gmail.com>
```

When you re-compiled did you run "git pull" and such as shown in [Updating ffmpeg](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide#update)?

> 
```
tim@tim-quad-core:~$ ffmpeg -f v4l2 -i /dev/video3 -codec copy -map 0 -f segment -segment_time 600 space/meteors_%04d.mkv
...
Could not write header for output file #0 (incorrect codec parameters ?): No such file or directory
```
My guess is that you need to make the space directory first: "mkdir space".

> Now to see if i can integrate the timecode into it.... 
Filtering the video requires re-encoding, so you will be unable to stream copy with "-codec copy". I recommend using the raw format from the camera as input instead of mjpeg, and then encoding with libx264:

```
ffmpeg -f video4linux2 -input_format yuyv422 -i /dev/video3 -vf "drawtext=fontfile=/usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf:text='Cline_sky_cam_west_':timecode='$(date +%H\\:%M\\:%S).00': r=30/1: x=(w-tw)/2: y=h-(1*lh): fontcolor=white: fontsize=16: box=1: boxcolor=0x00000999,format=yuv420p" -vcodec libx264 -preset medium -crf 18 -map 0 -movflags faststart -f segment -segment_time 600 space/meteors_%04d.mp4
```

---

### Post by timsdeepsky on 2013-09-18
I seem to have encountered a large problem when i re-installed ffmpeg from my usual source....
[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide#update]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide#update")....
Ffmpeg seems to install itself in  "/home/tim/bin",,,, and "home/tim/ffmpeg"  but not in " /usr/local/bin/ffmpeg" ....
My ffmpeg codes that were working before perfectly are now getting these errors.... ```
bash: /usr/local/bin/ffmpeg: No such file or directory
tim@tim-quad-core:~$ 
```
And my Zoneminder program that relies on ffmpeg has stopped working....
All of this happened at the same time,,after my attempt at re-installing and up-dating ffmpeg....
I will see what i can figure out....

[B]Update....I fixed Zoneminder but still can not get ffmpeg to install in my " /usr/local/bin/ffmpeg" folder using this link....
[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide#update]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide#update")....[/B]

---

### Post by timsdeepsky on 2013-09-20
I have not been able to get ffmpeg to install in  "/usr/local/bin/ffmpeg "....
It used to every time....
Now it will only install in my "/home/tim/bin/ffmpeg" folder....
All of my bash scripts were failing because they could not find ffmpeg in "/usr/local/bin/ffmpeg" like before....
So i changed the ffmpeg path to "/home/tim/bin/ffmpeg" and they work....
I am not sure what happened that changed my ffmpeg default install path....

---

### Post by timsdeepsky on 2013-09-21
This does work for me now....
```
ffmpeg -f video4linux2 -input_format yuyv422 -i /dev/video3 -vf "drawtext=fontfile=/usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf:text='Cline_sky_cam_west_':timecode='$(date +%H\\:%M\\:%S).00': r=30/1: x=(w-tw)/2: y=h-(1*lh): fontcolor=white: fontsize=16: box=1: boxcolor=0x00000999,format=yuv420p" -vcodec libx264 -preset medium -crf 18 -map 0 -movflags faststart -f segment -segment_time 30 space/meteors_%04d.mp4

```


I am closing this thread as my original issue was solved....
Thanks Fakeoutdoorsman....

---

### Post by qyot27 on 2013-09-22
The reason it isn't installing in /usr/local is because the compilation instructions specify a custom installation path.  This was discussed some a few months ago in the x264/FFmpeg compiling thread because there was a desire to avoid the use of checkinstall and system installation.

All you have to do to go back to installing in /usr/local is remove the --prefix= and --bindir= options when you ./configure FFmpeg.

---

### Post by timsdeepsky on 2013-09-22
No worries....I have always used this link to install ffmpeg....[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide#update]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide#update")
Every time before it would install by default in "/usr/local/bin/ffmpeg "....No problems at all....Then out of the blue it started installing in  "/home/tim/bin/ffmpeg"....
I never ran across this=```
All you have to do to go back to installing in /usr/local is remove the --prefix= and --bindir= options when you ./configure FFmpeg. 
```....So i just made the new path to ffmpeg and moved on....
Thanks for your help qyot27....

---

