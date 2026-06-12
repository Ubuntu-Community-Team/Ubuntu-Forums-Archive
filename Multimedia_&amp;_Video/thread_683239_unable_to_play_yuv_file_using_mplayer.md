---
title: "unable to play yuv file using mplayer"
date: 2008-01-30
forum: Multimedia &amp; Video
---

### Post by archana gopalan on 2008-01-30
hi all,

I have installed mplayer.I am trying to play a yuv video file(raw) using mplayer.But i get the following error
.................................................................................................................................
Playing /home/archana/Desktop/akiyo_qcif.yuv.
libavformat file format detected.
picture size invalid (0x0)
[rawvideo @ 0x87b9914]Could not find codec parameters (Video: rawvideo, yuv420p)
LAVF_header: av_find_stream_info() failed
....................................................................................................................................
Could anyone tell me what could be wrong?
Also if there is any other player that can play yuv file,please let me know.

Thanks
Archana

---

### Post by andrew.46 on 2008-01-30
Hi,

 Saw an mplayer problem:

> **archana gopalan said:**
> 
I have installed mplayer.I am trying to play a yuv video file(raw) using mplayer.But i get the following error
.................................................................................................................................
Playing /home/archana/Desktop/akiyo_qcif.yuv.
libavformat file format detected.
picture size invalid (0x0)
[rawvideo @ 0x87b9914]Could not find codec parameters (Video: rawvideo, yuv420p)
LAVF_header: av_find_stream_info() failed


According to the mplayer site it *should* play:

[http://www.mplayerhq.hu/design7/info.html](http://www.mplayerhq.hu/design7/info.html)

Can you post this file somewhere so I can try it with the svn mplayer?

              Andrew

---

