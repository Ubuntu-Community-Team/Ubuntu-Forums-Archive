---
title: "Completely new to Ubuntu - WINFF question"
date: 2012-07-01
forum: Multimedia Software
---

### Post by erichon on 2012-07-01
Hi everybody

I am completely new to Ubuntu and already have a problem: 
I like to output to H264 MOV with Winff, but the presets do not work. So I would like to make my own preset. Can anybody tell me, what Preset Command Line I have to put in?

I compiled ffmpeg from Medibuntu and the codecs as well.

Thx
Eric

---

### Post by ron999 on 2012-07-01
> **erichon said:**
> ... Can anybody tell me, what Preset Command Line I have to put in?

I compiled ffmpeg from Medibuntu and the codecs as well.

Hi
For **mov** files with **h264** video and **aac** audio..
This WinFF preset command works for *buntu 12.04 with medibuntu codecs
```
-vcodec libx264 -crf 23 -preset medium -acodec libfaac -aq 100 -ar 44100 -ac 2
```

---

### Post by erichon on 2012-07-07
Hmmm it does not work - it says??? Hard stuff for beginners.

[avi @ 0xad063e0] non-interleaved AVI
[avi @ 0xad063e0] Could not find codec parameters (Video: none (CHQX / 0x58514843), 1920x1080)
Guessed Channel Layout for  Input Stream #0.1 : stereo
Input #0, avi, from '/media/TOSHIBA EXT/TextHQXSuperfine.avi':
  Duration: 00:01:44.48, start: 0.000000, bitrate: 234606 kb/s
    Stream #0:0: Video: none (CHQX / 0x58514843), 1920x1080, 25 fps, 25 tbr, 25 tbn, 25 tbc
    Stream #0:1: Audio: pcm_s16le ([1][0][0][0] / 0x0001), 48000 Hz, stereo, s16, 1536 kb/s
[vbuffer source @ 0xad047a0] Unable to parse option value "-1" as pixel format
[buffer @ 0xad0d940] Error parsing options string: video_size=1920x1080:pix_fmt=-1:time_base=1/25:pixel_aspect=0/1:sws_param=flags=2:frame_rate=25/1.

---

### Post by erichon on 2012-07-07
And I would like that for Prores too. I found a command line:

  	 	 	 	 	 	   ffmpeg -i  "TextHQXSuperfine.avi" -vcodec prores -profile: 3 -acodec pcm_s24be -vf  setdar=16:9 -f mov  "TESTProRes.mov"  
  
but that does not work as well - suppose I am doing something wrong.

---

### Post by ron999 on 2012-07-07
> **erichon said:**
> Hmmm it does not work
[avi @ 0xad063e0] Could not find codec parameters (Video: none ([COLOR="Red"]CHQX[/COLOR] / 0x58514843), 1920x1080)

[vbuffer source @ 0xad047a0] Unable to parse option value "-1" as pixel format
[buffer @ 0xad0d940] Error parsing options string: video_size=1920x1080:[COLOR="Red"]pix_fmt=-1[/COLOR]:time_base=1/25:pixel_aspect=0/1:sws_param=flags=2:frame_rate=25/1.

Hi
What's your source video "TextHQXSuperfine.avi", does it use some proprietary codec?

---

