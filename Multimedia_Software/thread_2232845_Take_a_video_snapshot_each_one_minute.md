---
title: "Take a video snapshot each one minute"
date: 2014-07-04
forum: Multimedia Software
---

### Post by alfirdaous on 2014-07-04
Hello everybody,

I would like to get a thumbnail each 1 minute from a video, but it returns an error:

```

ffmpeg -i input.flv -f image2 -vf fps=fps=1 out%d.png
```

No such filter fps

this is the full code:

```

$ ffmpeg -i font_FreeSans.mp4 -f image2 -vf fps=fps=0.1 out%d.png
ffmpeg version 0.8.10-6:0.8.10-0ubuntu0.12.10.1, Copyright (c) 2000-2013 the Libav developers
  built on Feb  6 2014 20:57:40 with gcc 4.7.2
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'font_FreeSans.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    creation_time   : 2014-06-29 02:41:34
    encoder         : Lavf53.21.1
  Duration: 00:00:09.00, start: 0.000000, bitrate: 353 kb/s
    Stream #0.0(und): Video: h264 (Main), yuv420p, 576x360 [PAR 1:1 DAR 8:5], 251 kb/s, 25 fps, 25 tbr, 25 tbn, 50 tbc
    Metadata:
      creation_time   : 2014-06-29 02:41:34
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16, 96 kb/s
    Metadata:
      creation_time   : 2014-06-29 02:41:34
Incompatible pixel format 'yuv420p' for codec 'png', auto-selecting format 'rgb24'
[buffer @ 0x8342a00] w:576 h:360 pixfmt:yuv420p
No such filter: 'fps'
Error opening filters!



```

Thanks in advance

---

### Post by TheFu on 2014-07-05
This is what I found on the ffmpeg website:
ffmpeg -i myvideo.avi -f image2 -vf fps=fps=1/60 img%03d.jpg 

Don't know if it works. It didn't on my 1204 desktop with ffmpeg v0.8.12-4:0.8.12-0ubuntu0.12.04.1.  It appears that this command only works for the newest versions of ffmpeg.  
Reading the manpage for the version installed on my system, it found this style of the command which did work:
ffmpeg -i file.avi  -r 1 -s 640x480 -f image2 foo-%03d.jpeg

Hope this helps.

---

### Post by alfirdaous on 2014-07-08
@[**[COLOR=#000000]TheFu[/COLOR]**]("http://ubuntuforums.org/member.php?u=1037685"): It works perfect, the snapshot is taken each minute or each second?

---

