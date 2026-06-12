---
title: "howto : convert full hd (1920x1080 mpgv Frate50) to vob PAL"
date: 2013-03-02
forum: Multimedia Software
---

### Post by escobero on 2013-03-02
I used devede for years to calculate the ISO to burn.
I now grab in full hd and if I want to burn a dvd from my edited videos (to share with other poeple) I get a very poor (pixelated) result.

anyone out the to tell me how to get a clear/good(not pixelated) vob from a full hd video

in a precise case (transcoding in another HD format works well, only to VOB  is poor)
video codec: MPEG 1/2 Video (mpgv)
resolution: 1920x1080
framerate: 50
decoded format: Planar 4:2:0 YUV

audio codec: MPEG audio layer 1/2/3 (mpga)
channels: stereo
samplerate: 48000
Bitrate: 384k b/s

---

### Post by evilsoup on 2013-03-02
Is the frame rate *actually* 50 fps, or is it interlaced? Regardless, I would try ffmpeg with -target.

```

ffmpeg -i input.file -target pal-dvd output.vob

```

FFmpeg should calculate all the rescaling etc itself, and should output very good quality video with -target, in my experience.

---

### Post by escobero on 2013-03-03
you are right. the original is 
video:
H264 - MPEG-4 AVC(part10) (avc1)
1920x1080
25
planar 4:2:0 YUV

audio:
Codec: A52 Audio (aka AC3) (a52)
stereo
4800 Hz
256 kb/s

I suppose I could also convert this original (16 GB while the other file on which my question was based has 5GB, same video) with the same terminal line to vob

and more: ¿ may I suppose that I would be able to convert any xy.mov or xy.mp4 to vob by this method?

thanks for your response ... computer is calculating. 
I will tell you the outcome 

for now : Thanks a lot

---

### Post by escobero on 2013-03-03
you are right. the original is 
video:
H264 - MPEG-4 AVC(part10) (avc1)
1920x1080
25
planar 4:2:0 YUV

audio:
Codec: A52 Audio (aka AC3) (a52)
stereo
4800 Hz
256 kb/s

I suppose I could also convert this original (16 GB while the other fie o which my question was based has 5GB, same video) with the same terminal line to vob

and more: ¿ may I suppose that I would be able to convert any xy.mov or xy .mp4 to vob by this method?

thanks for your response ... computer is calculating. 
I will tell you the outcome 

for now : Thanks a lot

---

### Post by escobero on 2013-03-03
the computer just finished the process.

it is better, but not satisfying. there are still some pixelations, mostli in the shadow.

I'll convert the original file 16GB to see if the result is better

---

