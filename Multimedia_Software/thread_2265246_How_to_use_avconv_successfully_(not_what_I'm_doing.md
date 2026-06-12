---
title: "How to use avconv successfully (not what I'm doing right now)."
date: 2015-02-13
forum: Multimedia Software
---

### Post by Bobby_James on 2015-02-13
I have various mov files from recording with my camera. They are large: 4 minutes comes in at 500MB.

I have tried using avconv to convert to avi and mpg formats but the file size is still around 250MB.

I use:

```
avconv -i movie.mov -vcodec libx264 -acodec libmp3lame -ac 2 movie.mp4
```

I would really like to get the mov file into a maneagble state. I have downloaded films of 90 minutes which are 700MB in avi or mpg format. I don't understand why my 4 minute movie is so massive

Of course, I would like minimum loss of quality.

Thank you!

---

### Post by andrew.46 on 2015-02-14
Could you give the complete output from:

```

avconv -i movie.mov

```

Shouldn't be too hard to trim this monster a little :)

---

### Post by Bobby_James on 2015-02-14
Thanks for your suggestion. Output below. The current file size is 479MB.


```
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'REC_0018.MOV':
  Metadata:
    major_brand     : qt  
    minor_version   : 0
    compatible_brands: qt  
    creation_time   : 2004-01-01 00:00:00
  Duration: 00:03:29.00, start: 0.000000, bitrate: 18342 kb/s
    Stream #0.0(eng): Video: h264 (High), yuv420p, 1920x1080, 17688 kb/s, 30 fps, 30 tbr, 30k tbn, 60k tbc
    Metadata:
      creation_time   : 2004-01-01 00:00:00
    Stream #0.1(eng): Audio: pcm_s16le, 32000 Hz, 1 channels, s16, 512 kb/s
    Metadata:
      creation_time   : 2004-01-01 00:00:00

```

---

### Post by SeijiSensei on 2015-02-14
> bitrate: 18342 kb/s
I suspected your camera might have a high bitrate.  Even the camera on my smartphone runs at about 16 Kbit/sec.  I just looked at a movie rip and its bitrate was around 7000.  Apparently you can set the bitrate in avconv with the -b switch.  Try "-b 8K" and see what size file you get and whether it is still of decent quality.

---

### Post by andrew.46 on 2015-02-14
Perhaps some experimentation with 2 pass:

[https://trac.ffmpeg.org/wiki/Encode/H.264#twopass](https://trac.ffmpeg.org/wiki/Encode/H.264#twopass)

---

### Post by Bobby_James on 2015-02-14
"-b 8K" looked awful. It was just a series of blobs moving around. However, "-b 1024K" looked identical to the original and was 49MB which is 10% of the original size. I appreciate your advice as the "-b" option really reduced the filesize.

How would you define the bitrate in layman's terms? I was using a Mobius camera at 1080p 30fps.

---

### Post by SeijiSensei on 2015-02-14
This was pretty informative: [https://www.youtube.com/watch?v=QOn-9anLFxA](https://www.youtube.com/watch?v=QOn-9anLFxA)

You might also try playing with the -fs ("file size") option.  You can set a target file size, and avconv will choose a bitrate.  

As the YouTube video mentions, you can choose [variable bit rates]("http://superuser.com/questions/556463/converting-video-to-webm-with-ffmpeg-avconv") if the material varies a lot in compressibility.  Also there's the option of multiple passes as andrew mentions.  I don't convert files much any more, but when I was converting with the older XviD codec using two passes made a noticeable improvement to quality.

---

### Post by FakeOutdoorsman on 2015-02-14
> **andrew.46 said:**
> Perhaps some experimentation with 2 pass:

[https://trac.ffmpeg.org/wiki/Encode/H.264#twopass](https://trac.ffmpeg.org/wiki/Encode/H.264#twopass)

Just a note for other users that the FFmpeg Wiki pages are written for ffmpeg from FFmpeg, so avconv will not always work.

---

