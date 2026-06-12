---
title: "HTML 5 Video Problem"
date: 2012-12-07
forum: Multimedia Software
---

### Post by nclucid on 2012-12-07
Hey Everyone, I hope someone can help me out...

I have a website that streams html5 video (mp4). It was literally working just last night, and suddenly stopped and I can't figure out why. See some code and video info below. If anyone has any ideas I would be grateful!

```

$ ffmpeg -i 'The Walking Dead S03E08 HDTV x264 [GlowGaze.Com].mp4'
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'The Walking Dead S03E08 HDTV x264 [GlowGaze.Com].mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isomavc1
    creation_time   : 2012-12-03 03:06:47
  Duration: 00:43:19.55, start: 0.000000, bitrate: 1102 kb/s
    Stream #0:0(und): Video: h264 (High) (avc1 / 0x31637661), yuv420p, 720x404 [SAR 1:1 DAR 180:101], 979 kb/s, 23.98 fps, 23.98 tbr, 96k tbn, 47.95 tbc
    Metadata:
      creation_time   : 2012-12-03 03:06:47
    Stream #0:1(und): Audio: aac (mp4a / 0x6134706D), 48000 Hz, stereo, s16, 119 kb/s
    Metadata:
      creation_time   : 2012-12-03 03:06:49
At least one output file must be specified

``````

<video src="[/links/50407b82296ff56eba3c8c494e399939.mp4]("http://ubuntuforums.org/view-source:http://192.168.0.198/links/50407b82296ff56eba3c8c494e399939.mp4")" width="700px" height="400px" controls poster="/images/poster.jpg" preload="auto" class="video-js vjs-default-skin" data-setup="{}">   <span style="font: bold 32px Arial, Helvetica, sans-serif; color: #fff;">Something went wrong....</span> </video>

```If you take out the "data-setup" option of the video tag, "Video format or mime type not supported" shows up. Except it IS supported! If I point my browser directly to the file it plays no problem (in firefox).

Like I said, this was working just last night. I am baffled as to what changed... Please, any suggestions?

---

### Post by upandacross on 2013-05-23
I was working on playing mp4 files in an ipython notebook. After installing mozilla-plugin-vlc, I am able to display an HTML tag to launch the vlc player and play an mp4 file. Find the python code at [http://snipt.org/Aagv8](http://snipt.org/Aagv8)

---

### Post by gordintoronto on 2013-05-23
From what I can see, the servers at glowgaze.com are not up to the job. Or maybe they don't have enough bandwidth. In any case, the site is not very responsive, with most clicks failing in Google Chrome.

---

