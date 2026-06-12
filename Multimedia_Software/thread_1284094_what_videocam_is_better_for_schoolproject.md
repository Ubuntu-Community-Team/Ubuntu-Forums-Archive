---
title: "what videocam is better for schoolproject"
date: 2009-10-06
forum: Multimedia Software
---

### Post by mibungu on 2009-10-06
HI, I searched a bit for compatibility etc..

I use ubuntu (9.04) and am used to capture with kino and edit with cinelerra, but don't own that cam anymore

I'm a dramateacher participating in a youthproject.And making some film spots about awareness, drugs, social problems,etc.. Not for professional use but should look good !
The foundation doesn't have alot of financial resources so I have to watch the budget. 

I need some advice on which videocams to purchase. I live on a touristic Island so the new  vidcams are available and will do  , something between $300-600. But which is better. Since kino doesn't capture hdv, some vcams render in mp4, etc.,etc..

Does anyone have any advice pls.

I'm gonna use my own laptop with the apps mentioned above and I don't want to tell the coordinator to buy something which I won't be able to use.

Thanx,


Mi bun g u:guitar:
I am good for U !

---

### Post by RedRat on 2009-10-06
While it is true that Ubuntu seems to be lacking for HD support, I believe that this is slowly changing, especially since you are on 9.04. I believe that Kino or kdenlive or cinellera may be supporting HD in 9.04.  I note that Lives supports HD, ie. hdv. You might want to check out their respective web site. 

I have a Canon Vexia HD camera and lives seems to be able to take in some hd, but limited resolution. Give it a shot for your Ubuntu 9.04. I note that 8.04 doesn't seem to be getting much attention because it will be supplanted in about 6 months with the new LTS verison of Ubuntu (10.4).

I would think now that HD TVs are becoming more of a reality in every day homes, you might want to consider taping in HD format. You can always dumb down (down convert) the resolution, but it is very difficult up-converting to HD and have the images really look good.

---

### Post by mibungu on 2009-10-17
Well , that's almost no advise. I guess I'll just risk it which i don't want. I know what to do but, anyway. NO hdv with kino at least. :(

---

### Post by ejolson on 2009-10-18
> **mibungu said:**
> Well , that's almost no advise. I guess I'll just risk it which i don't want. I know what to do but, anyway. NO hdv with kino at least. :(

I would reserve part of the budget for microphones, lighting, a tripod and a monopod.  With proper lighting almost any camcorder will give a picture good enough for a standard definition DVD.  Since you will be recording dialog and interviews, microhpones and a camcorder with a microphone input is essential.

All HDV camcorders can be set to DV output mode which allows them to work with video capture devices such as Kino.  You can also use dvgrab to capture HDV and then edit it on Cinelerra.  A refurbished Canon HV30 is about $600 right now.

AVCHD camcorders produce files that must be transcoded before editing.  You can transcode AVCHD into DV for Kino using the command
```

ffmpeg -i 00023.mts -r 30000/1001 -acodec pcm_s16le -vcodec dvvideo \
    -deinterlace -pix_fmt yuv411p -s 720x480 \
    -aspect 16:9 -f dv -y 00023.dv
```
A similar command will transcode AVCHD into high definition HDV that can be edited with Cinelerra.  The Canon HF200 is new for about $600.  The Canon HG10 is available refurbished for about $400.

Since you are making a DVD all you need is a standard definition video camera.  A new Canon ZR960 is about $250 and is the only consumer miniDV camcorder currently manufactured that has microphone inputs.

More information about using Linux for video editing can be found at

[http://www.renomath.org/ejolson/video/](http://www.renomath.org/ejolson/video/)

---

### Post by RedRat on 2009-10-18
> **ejolson said:**
> I would reserve part of the budget for microphones, lighting, a tripod and a monopod.  With proper lighting almost any camcorder will give a picture good enough for a standard definition DVD.  Since you will be recording dialog and interviews, microhpones and a camcorder with a microphone input is essential.

All HDV camcorders can be set to DV output mode which allows them to work with video capture devices such as Kino.  You can also use dvgrab to capture HDV and then edit it on Cinelerra.  A refurbished Canon HV30 is about $600 right now.

AVCHD camcorders produce files that must be transcoded before editing.  You can transcode AVCHD into DV for Kino using the command
```

ffmpeg -i 00023.mts -r 30000/1001 -acodec pcm_s16le -vcodec dvvideo \
    -deinterlace -pix_fmt yuv411p -s 720x480 \
    -aspect 16:9 -f dv -y 00023.dv
```A similar command will transcode AVCHD into high definition HDV that can be edited with Cinelerra.  The Canon HF200 is new for about $600.  The Canon HG10 is available refurbished for about $400.

Since you are making a DVD all you need is a standard definition video camera.  A new Canon ZR960 is about $250 and is the only consumer miniDV camcorder currently manufactured that has microphone inputs.

More information about using Linux for video editing can be found at

[http://www.renomath.org/ejolson/video/](http://www.renomath.org/ejolson/video/)

Thanks very much for the web site and other info. I think you are right on target. There is some very good info on that site.:popcorn:

---

### Post by mibungu on 2009-10-19
Thanx alot Ejolson that just cleared it up for me. Now I can tell the coordinator what to do. :popcorn:

I'll check the site asap and get on with the schoolproject

Mibungu!:P

---

### Post by mibungu on 2009-11-03
Is it necessary to rebuild ffmpeg or not 

ffmpeg -i 00003.MTS -r 30000/1001 -acodec pcm_s16le -vcodec dvvideo -deinterlace -pix_fmt yuv411p -s 720x480 -aspect 16:9 -f dv -y 00023.dv


cause I get thi error
ffmpeg -i 00003.MTS -r 30000/1001 -acodec pcm_s16le -vcodec dvvideo -deinterlace -pix_fmt yuv411p -s 720x480 -aspect 16:9 -f dv -y 00023.dvFFmpeg version git-91be88c, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-shared --enable-pthreads --enable-libx264 --enable-libfaac --enable-libtheora
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.20. 0
  libavformat   52.36. 0 / 52.31. 0
  libavdevice   52. 2. 0 / 52. 1. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Jul 24 2009 21:22:03, gcc: 4.3.3
Input #0, mpegts, from '00003.MTS':
  Duration: 00:00:10.01, start: 1.000067, bitrate: 5888 kb/s
  Program 1 
    Stream #0.0[0x1011], 1/90000: Video: h264, yuv420p, 1440x1080 [PAR 4:3 DAR 16:9], 1001/60000, 59.94 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x1100], 1/90000: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
ffmpeg: symbol lookup error: ffmpeg: undefined symbol: avcodec_channel_layout_num_channels

---

### Post by mibungu on 2009-11-03
So I have to compile ffmpeg with h265 support rite ?

---

