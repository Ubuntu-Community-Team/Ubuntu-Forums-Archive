---
title: "ffmpeg ubuntu gpu support"
date: 2019-01-06
forum: Multimedia Software
---

### Post by chalan2 on 2019-01-06
hello, can somebody advise me gpu card which have support for h254 and h265 in linux/ubuntu? i need to encode lot of mxf and gxf files into h264 and h265.

---

### Post by mc4man on 2019-01-07
[https://developer.nvidia.com/video-encode-decode-gpu-support-matrix](https://developer.nvidia.com/video-encode-decode-gpu-support-matrix)
(- list can be expanded 
note that quality can suffer with gpu encoding

---

### Post by chalan2 on 2019-01-09
quality loss compared to accelaration? is it worth to buy gpu just for h265 encoding? lets just say a cpu encoding last 3hour, how fast will it be with gpu?

---

### Post by mc4man on 2019-01-09
> **chalan2 said:**
> quality loss compared to accelaration? is it worth to buy gpu just for h265 encoding? lets just say a cpu encoding last 3hour, how fast will it be with gpu?
Time would depend on what settings you use, I'd say if 3 hr on cpu then less than 2 on gpu.
Just find best settings to achieve what you wish..
(- here my gpu doesn't do hevc, on h.264 nvenc can do pretty well. There are many pages that will give you possible encoding settings, just search out..

It's possible the default Ubuntu repo ffmpeg doesn't do nvenc, if not there are many ways around that..

---

