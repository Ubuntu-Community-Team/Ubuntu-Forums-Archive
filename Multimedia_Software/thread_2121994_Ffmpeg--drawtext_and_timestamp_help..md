---
title: "Ffmpeg--drawtext and timestamp help."
date: 2013-03-03
forum: Multimedia Software
---

### Post by timsdeepsky on 2013-03-03
Well i am confused once again....
I use cron to call this bash script,,
```
#!/bin/bash
/usr/local/bin/ffmpeg -framerate 25 -f video4linux2 -video_size 656x492 -i /dev/video2 -t 02:00:00 -vf drawtext="fontfile=/usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf:text='Sky_cam_west_':timecode='05\:00\:00\:00': r=23.976: x=(w-tw)/2: y=h-(1*lh): fontcolor=white: fontsize=16: box=1: boxcolor=0x00000999" -vcodec libx264 -preset slow -crf 28 -movflags faststart -acodec libfaac -aq 100 /home/tim/bin/sunset_cronkilltoo.mp4


```
I re-installed ffmpeg,,x264 and all else from here [https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide")
and enabled libfreetype,and **am** able to make this work well....
It starts the timecode overlay from 5 o'clock because i physically
type it in('05\:00\:00\:00')....
Problem =I want it to pull my local time and overlay on the video automatically....
I have tried numerous codes from numerous pages from my search including 
[http://ffmpeg.org/trac/ffmpeg/wiki/FilteringGuide]("http://ffmpeg.org/trac/ffmpeg/wiki/FilteringGuide")
[https://gist.github.com/reidransom/2630650]("https://gist.github.com/reidransom/2630650")
[http://ffmpeg.org/ffmpeg-filters.html#drawtext-1]("http://ffmpeg.org/ffmpeg-filters.html#drawtext-1")
[https://ffmpeg.org/trac/ffmpeg/wiki/EncodeforYouTube]("https://ffmpeg.org/trac/ffmpeg/wiki/EncodeforYouTube")
and so on....
The code below
```
#!/bin/bash
/usr/local/bin/ffmpeg -framerate 25 -f video4linux2 -video_size 656x492 -i /dev/video2 -t 02:00:00 -vf drawtext="fontfile=/usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf:text='Sky_cam_west_':timecode='\%H\:\%M\:\%S | \%a \%d/\%b/\%Y': r=23.976: x=(w-tw)/2: y=h-(1*lh): fontcolor=white: fontsize=16: box=1: boxcolor=0x00000999" -vcodec libx264 -preset slow -crf 28 -movflags faststart -acodec libfaac -aq 100 /home/tim/bin/sunset_cronkilltoo.mp4

```
Gives me this error 
```
tim@tim-quad-core:~$ ffmpeg -framerate 25 -f video4linux2 -video_size 656x492 -i /dev/video2 -t 02:00:00 -vf drawtext="fontfile=/usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf:text='Sky_cam_west_':timecode='\%H\:\%M\:\%S | \%a \%d/\%b/\%Y': r=23.976: x=(w-tw)/2: y=h-(1*lh): fontcolor=white: fontsize=16: box=1: boxcolor=0x00000999" -vcodec libx264 -preset slow -crf 28 -movflags faststart -acodec libfaac -aq 100 /home/tim/bin/sunset_cronkilltoo.mp4
ffmpeg version N-43174-gf4e29c4 Copyright (c) 2000-2013 the FFmpeg developers
  built on Mar  3 2013 08:05:54 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --enable-gpl --enable-libass --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libspeex --enable-librtmp --enable-libtheora --enable-libvorbis --enable-libvpx --enable-x11grab --enable-libx264 --enable-libfreetype --enable-nonfree --enable-version3
  libavutil      52. 17.102 / 52. 17.102
  libavcodec     54. 92.100 / 54. 92.100
  libavformat    54. 63.100 / 54. 63.100
  libavdevice    54.  3.103 / 54.  3.103
  libavfilter     3. 38.103 /  3. 38.103
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100
[video4linux2,v4l2 @ 0x2831540] The V4L2 driver changed the video from 656x492 to 656x480
[video4linux2,v4l2 @ 0x2831540] The driver does not allow to change time per frame
[video4linux2,v4l2 @ 0x2831540] Estimating duration from bitrate, this may be inaccurate
Input #0, video4linux2,v4l2, from '/dev/video2':
  Duration: N/A, start: 1362355236.726727, bitrate: 113243 kb/s
    Stream #0:0: Video: rawvideo (I420 / 0x30323449), yuv420p, 656x480, 113243 kb/s, 29.97 fps, 29.97 tbr, 1000k tbn, 1000k tbc
[Parsed_drawtext_0 @ 0x2835c60] Unable to parse timecode, syntax: hh:mm:ss[:;.]ff
[AVFilterGraph @ 0x2838900] Error initializing filter 'drawtext' with args 'fontfile=/usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf:text=Sky_cam_west_:timecode=\%H\:\%M\:\%S | \%a \%d/\%b/\%Y: r=23.976: x=(w-tw)/2: y=h-(1*lh): fontcolor=white: fontsize=16: box=1: boxcolor=0x00000999'
Error opening filters!
tim@tim-quad-core:~$ 
```
Thanks for any link or advice you may have....I will continue on with it in the meantime....

---

### Post by FakeOutdoorsman on 2013-03-04
Try this:
```
timecode='$(date +%H\\:%M\\:%S).00'
```

I think this will provide what you're looking for, but I wasn't totally sure. The escaping is confusing and there is probably a more elegant solution.

Other stuff:
> **timsdeepsky said:**
> ```
[video4linux2,v4l2 @ 0x2831540] The V4L2 driver changed the video from 656x492 to 656x480
```
Did you see this message?

> **timsdeepsky said:**
>  Stream #0:0: Video: rawvideo (I420 / 0x30323449), yuv420p, 656x480, 113243 kb/s, 29.97 fps, 29.97 tbr, 1000k tbn, 1000k tbc[/code]

You delcare -framerate 25, but your input is showing 29.97 (or more specifically, 30000/1001), and using "r=23.976" in your filter may cause issues. Frame size appears to be 656x480, not 656x492.

---

### Post by timsdeepsky on 2013-03-04
Thanks FakeOutdoorsman....This worked perfect....Sometimes i search and look at enough pages and try changing the code so many times i get a brain fog going....Ffmpeg gets me confused sometimes....You are right about the framerate....I changed it to 29.97 and 30000/1001 and they both seem to work,,so i left it as 30000/1001(is this right??..or should i leave it at 29.97??..)....I changed the frame size also....I had that frame size because when i messed with this particular camera in zoneminder,,it seemed to show them numbers for some reason....I just took it for granted....Eventually i want all my meteor cameras weaned off of the gui's i use now,,and running with all ffmpeg code at my control....Thanks once again for all you do for all of us in the forums....

---

### Post by FakeOutdoorsman on 2013-03-05
> **timsdeepsky said:**
> Thanks FakeOutdoorsman....This worked perfect....Sometimes i search and look at enough pages and try changing the code so many times i get a brain fog going....Ffmpeg gets me confused sometimes....
Yes, the syntax can be tricky. Luckily I was working at a retail location and had a good amount of free time (I'm just the backup to the backup worker, so I'm only there once a month or less).

> **timsdeepsky said:**
> You are right about the framerate....I changed it to 29.97 and 30000/1001 and they both seem to work,,so i left it as 30000/1001(is this right??..or should i leave it at 29.97??..)
Use 30000/1001. 29.97 isn't quite the NTSC video frame rate. You could possibly use the "ntsc" alias (r=ntsc), but I'm not sure if that works in filters.

> **timsdeepsky said:**
> ....I changed the frame size also....I had that frame size because when i messed with this particular camera in zoneminder,,it seemed to show them numbers for some reason....
You can always probe the camera and see what it supports with:
```
ffmpeg -f v4l2 -list_formats all -i /dev/video2
```
or
```
v4l2-ctl --list-formats-ext
```

> **timsdeepsky said:**
> I just took it for granted....Eventually i want all my meteor cameras weaned off of the gui's i use now,,and running with all ffmpeg code at my control....Thanks once again for all you do for all of us in the forums....
Sound like an interesting project. I've always wanted to try some astrophotography timelapses on a slow rail setup, but it is more cloudy than clear here.

---

### Post by timsdeepsky on 2013-03-05
Astrophotography is awesome....I have a small observatory that i built next to my house,,and take images with a ccd imager....I have numerous pics of Galaxies,,Nebula,,Comets,,etc on my site[http://timcline.org/]("http://timcline.org/")....Added 2 home built meteor cams to it in late 2009....These cams are what i usually experiment with ffmpeg on....Good times....Thanks for all....

---

