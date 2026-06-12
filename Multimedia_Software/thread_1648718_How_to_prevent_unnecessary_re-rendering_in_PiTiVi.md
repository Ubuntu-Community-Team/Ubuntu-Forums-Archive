---
title: "How to prevent unnecessary re-rendering in PiTiVi"
date: 2010-12-19
forum: Multimedia Software
---

### Post by p_n on 2010-12-19
Hi,

I have a JVC Everio video camera that records directly DVD compliant mpeg files. Does anyone have a solution how to prevent re-rendering the files since that takes a lot of time and usually the end result is worse than the original one...

If PiTiVi does not enable this can anyone propose some other program to do this?

br, Petri

---

### Post by BicyclerBoy on 2010-12-20
You have problem opening the input clips right ?

I not a video editing expert but I used PiTiVi once.

I think you need to pick the correct output (export) container & the correct video/audio codecs.

DVDs use mpeg2 PS container in files called VOBs & the video must be mpeg2, the audio can be various things mp2 mp3 AC3.
The mpeg2 file has to be smaller than 1G, hence lots of VOBs for one movie.

The container to try would be mpeg2 ffmpeg PS format (DVD VOB) muxer.
mp2 audio is fine (better than mp3).

The only rendering will then be credits/images/extra stuff.
I think additional I frames will have to be created at all cut-join points.

The default is Ogg Theora because it is free open source.
Transcoding between different lossy compressed data formats is bad for PQ.

---

### Post by BicyclerBoy on 2010-12-20
I have not able to discover the internal data formats used by PiTiVi.
But I would think it would be something like MXF or some mjpeg using a TS container.

So there will (almost) always be a transcoding of input to a uniform efficient data format.
Video uses various frame & multi-frame compression techniques. These do not suit video editing. 

Avidemux will let you cut a mpeg-2 PS directly AFAIK. 

Nero has commercial software for linux & it might use the GPU (nvidia).

---

