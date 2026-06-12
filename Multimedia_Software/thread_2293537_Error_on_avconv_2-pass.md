---
title: "Error on avconv 2-pass"
date: 2015-09-05
forum: Multimedia Software
---

### Post by johny why on 2015-09-05
with 2-pass, i'm getting:
> $ avconv -i run.mp4 -pass 1 -vn -y -passlogfile run.log /dev/null
avconv version 9.18-6:9.18-0ubuntu0.14.04.1, Copyright (c) 2000-2014 the Libav developers
  built on Mar 16 2015 13:19:10 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'run.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: isommp42
    creation_time   : 2015-02-07 18:18:58
  Duration: 00:06:02.11, start: 0.000000, bitrate: 656 kb/s
    Stream #0.0(und): Video: h264 (High), yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 462 kb/s, 29.97 fps, 29.97 tbr, 30k tbn, 59.94 tbc
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, fltp, 191 kb/s
    Metadata:
      creation_time   : 2015-02-07 18:18:59
**Unable to find a suitable output format for '/dev/null'**

thx for any help.

---

### Post by TheFu on 2015-09-05
Don't use 2-pass encoding. I stopped using it about 3 yrs ago when h.264 become easily available.  Do you need xvid or mpeg2v4 output?

Use "constant quality" encoding for better results.

Also, use **ffmpeg**, not avconv. Things like this tend to work better with ffmpeg; don't know why.  Yesterday, I posted a conversion script in these forums. Should be easy to find and tweak for your needs.  Quality values of 19 are **insanely great**.  19.5 doesn't show any artifacts, but 20 begins to for high-action scenes.  You can also control the file compression levels using presets in ffmpeg. This impacts transcoding fps more than anything else, IME.
```

 FF_OPTS="-vcodec libx264 -crf 19 -vf scale=-1:720 -preset medium -strict experimental -c:a aac "
nice ffmpeg -y -i file-in.mpeg2 $FF_OPTS  file-out.mkv
```
You get the idea.

---

### Post by johny why on 2015-09-05
thx, but this is for conversion to audio-only mp3, so i think your suggestions about video would not apply. Is h.264 for audio mp3's?

---

### Post by TheFu on 2015-09-05
I'd use mplayer for that - not a 2-pass video encoding.  Is there a specific reason for the 2-pass video?

Something like ... 
```
#!/bin/bash
nice mplayer -ao pcm:waveheader -vc null -vo null $1 -ao pcm:fast:file=$1.wav
nice lame --preset mw-us $1.wav
rm $1.wav
```

Haven't used in this in awhile. Or something like ....

I suspect **ffmpeg -i file.mp4 file.mp3** would do what you want.

---

### Post by johny why on 2015-09-05
my understanding is that the 2-pass process optimizes the conversion, re size and quality. 

is that incorrect?

---

### Post by mc4man on 2015-09-05
Then  copy the audio only out to a file & do as you please converting to mp3
(I think very few see value in 2 pass mp3 encoding, do a web search
1 ex. [http://www.hydrogenaud.io/forums/index.php?showtopic=49127](http://www.hydrogenaud.io/forums/index.php?showtopic=49127)

---

