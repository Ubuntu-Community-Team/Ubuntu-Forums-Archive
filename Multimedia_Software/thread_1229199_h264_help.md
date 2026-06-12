---
title: "h264 help"
date: 2009-08-01
forum: Multimedia Software
---

### Post by DGortze380 on 2009-08-01
Ok. I know nothing about video encoding.

I have an .mp4
I have ffmpeg and mencoder installed

I need to convert this .mp4 to an h.264/mp4 for progressive download.

I thought I had it with the following, but flowplyer is telling me the file isn't found when I try to embed it.

```

mencoder cjs540.mp4 -oac mp3lame -ovc x264 -x264encopts bitrate=3000 -o cjs540_h264.mp4

```

Help please.

---

### Post by Revolutionary101 on 2009-08-01
You most likely entered the path to the file wrong. Because as you have it the file should be located at /home/user/cjs540.mp4

---

### Post by DGortze380 on 2009-08-01
Figures... found my answer right after I posted ...

for anyone else looking: [http://h264.code-shop.com/trac/wiki/Encoding](http://h264.code-shop.com/trac/wiki/Encoding)

---

### Post by DGortze380 on 2009-08-01
> **Revolutionary101 said:**
> You most likely entered the path to the file wrong. Because as you have it the file should be located at /home/user/cjs540.mp4

Nope, file path was definitely right, it was an encoding problem. Thanks though.

---

### Post by Revolutionary101 on 2009-08-01
No problem.

---

### Post by andrew.46 on 2009-08-01
Hi DGortze380,

> **DGortze380 said:**
> for anyone else looking: [http://h264.code-shop.com/trac/wiki/Encoding](http://h264.code-shop.com/trac/wiki/Encoding)

Mind you if you update your version of FFmpeg:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

you will be able to use the FFmpeg *presets* for x264 encoding which substantially lessen the pain as well as the length of the encoding string :-).

Andrew

---

### Post by DGortze380 on 2009-08-01
> **andrew.46 said:**
> Hi DGortze380,



Mind you if you update your version of FFmpeg:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

you will be able to use the FFmpeg *presets* for x264 encoding which substantially lessen the pain as well as the length of the encoding string :-).

Andrew

Good to know. It's going in a script anyways, so doesn't matter much to me .. but definitely a good resource.

Thanks

---

