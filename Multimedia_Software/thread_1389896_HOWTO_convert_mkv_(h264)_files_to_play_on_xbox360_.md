---
title: "HOWTO: convert mkv (h264) files to play on xbox360 or ps3"
date: 2010-01-25
forum: Multimedia Software
---

### Post by littlespy on 2010-01-25
I was looking for a method to convert h264 files to play on my xbox360 and I found a simple way to use mencoder to convert the files to avi.

```

mencoder <input> -channels 6 -ovc xvid -xvidencopts pass=1:threads=4:quant_type=mpeg:bitrate=-1500000 -vf harddup -oac copy -o /dev/null

mencoder <input> -channels 6 -ovc xvid -xvidencopts pass=2:threads=4:quant_type=mpeg:bitrate=-1500000 -vf harddup -oac copy -o <output>

```

This method uses 2 pass encoding and if you specify a negative bitrate it will tell mencoder to make the file that size in bytes, so you can play around with it.  There is some loss of quality, but I can't really notice it.

You only need to do this for h264, a lot of mkv files can be rewrapped in an avi container without re-encoding.

---

### Post by VertexPusher on 2010-01-25
Most H.264 files will play on XBox360 and PS3 without re-encoding. But you have to wrap them in MP4 containers and make sure that the audio track is AAC. AVI works only for MPEG-4 ASP video (i.e. DivX 5/6, Xvid) with MP3 audio.

---

### Post by littlespy on 2010-01-25
> **VertexPusher said:**
> Most H.264 files will play on XBox360 and PS3 without re-encoding. But you have to wrap them in MP4 containers and make sure that the audio track is AAC. AVI works only for MPEG-4 ASP video (i.e. DivX 5/6, Xvid) with MP3 audio.

i've heard that to, but i've never been successful in getting any H.264 files to play on my xbox :( even wrapped in mp4

---

### Post by btarlinian on 2010-01-25
I've found that the best solution for MKVs on the PS3 is to remux the streams into M2TS files using tsMuxer. These work as long as audio is AC-3 (Dolby Digital) or AAC and the video is H.264. If the audio is not AC-3, you can demux the mkv with mkvextract or tsMuxer, transcode the DTS audio into AC-3 or AAC, and remux the audio and video into an m2ts with tsMuxer.

---

