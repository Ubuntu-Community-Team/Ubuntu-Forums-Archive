---
title: "HD mp4 playback on Totem"
date: 2010-10-30
forum: Multimedia Software
---

### Post by zeevb on 2010-10-30
Totem has a problem playing HD mp4 videos that I download directly out of my Sony camera. I do not get any specific error, the player's screen remains black.
Reading in the forums I've seen the following procedure and tried it out:
First I ran mp4info:
```
$mp4info MAH00149.MP4 
mp4info version 1.6
MAH00149.MP4:
Track	Type	Info
1	video	H264 Main@4, 61.061 secs, 12010 kbps, 1440x1080 @ 29.970030 fps
2	audio	MPEG-4 AAC LC, 61.056 secs, 128 kbps, 48000 Hz
```
Then I ran the following commands:
```
$mp4creator -extract=1 MAH00149.MP4 video.264
mp4creator -extract=2 MAH00149.MP4 audio.aac
MP4Box -fps 29.970030 -cat video.264 -cat audio.aac -new newvideo.mp4 -inter 0 -keepsys

``` 
The new video (newvideo.mp4) plays without problems on Totem. As far as I understand this procedure extracts the audio and video tracks and merges them back into an mp4. Why only this mp4 plays back on Totem is a mystery to me.
mp4info gives the exact same output for the converted mp4 (nnewvideo.mp4)

Any ideas why this procedure helps?

---

### Post by HDave on 2011-01-12
Ever find out why?  Very curious myself...

---

