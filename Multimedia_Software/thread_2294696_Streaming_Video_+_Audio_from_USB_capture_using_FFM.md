---
title: "Streaming Video + Audio from USB capture using FFMPEG"
date: 2015-09-12
forum: Multimedia Software
---

### Post by uniquegodwin on 2015-09-12
I really need some help with using FFMPEG to stream video and audio together through RTMP .I've overclocked my raspi 2 and tried as much as I could so far.


The video streams fine but I can't hear any audio. I just hear random click sounds.Please help :


    
```
ffmpeg -f video4linux2 -channel 1 -i /dev/video0 -f alsa -i plughw:2,0 -r 25 -vcodec libx264 -strict experimental -acodec aac -b:a 20k -b:v 200k -aspect 4:3 -s 320x260 -ar 16000 -ab 32k -async 1 -g 6 -threads 4 -f flv rtmp://server:1935/live/test1



```

Any advise on how I should change this to make it work? I am trying this from a Ubuntu Mate on a raspberry pi 2 Model B. All I need is to successfully stream audio+video at this quality since I'm making it work through slow internet connections.


Thanks.

---

