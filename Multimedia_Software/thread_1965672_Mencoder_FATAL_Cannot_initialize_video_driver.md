---
title: "Mencoder FATAL: Cannot initialize video driver"
date: 2012-04-26
forum: Multimedia Software
---

### Post by CoximusPrime on 2012-04-26
Hi guys, I seem to have a strange problem when scaling using mencoder ... if I run this command :

```
mencoder movie.mkv -vf scale=1280:-2,pullup,pp=md,softskip,harddup -nosound -ovc x264 -x264encopts bitrate=1844:subq=4:bframes=3:b_pyramid=normal:weight_b:turbo=1:threads=auto:pass=1 -ofps 24000/1001 -o /dev/null
```

every thing is fine ... However if I try and reduce the movie to a lower resolution such as 720 using this command :

```
mencoder movie.mkv -vf scale=720:-2,pullup,pp=md,softskip,harddup -nosound -ovc x264 -x264encopts bitrate=1844:subq=4:bframes=3:b_pyramid=normal:weight_b:turbo=1:threads=auto:pass=1 -ofps 24000/1001 -o /dev/null
```

I get the following 

[swscaler @ 0x7fd34f6fc660]BICUBIC scaler, from yuv420p to yuv420p using MMX2
[swscaler @ 0x7fd34f6fc660]using n-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0x7fd34f6fc660]using n-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0x7fd34f6fc660]using n-tap MMX scaler for vertical scaling (YV12 like)
[swscaler @ 0x7fd34f6fc660]1920x816 -> 720x306
FATAL: Cannot initialize video driver.

Can anybody shed some light on this??

---

### Post by BicyclerBoy on 2012-04-26
I have a suspicion that the video frame sizes need to be multiples of 8 or 16 depending on the codec etc.

The swscaler routines might not like 306. Try 312 or 304 (16*19).

I think mencoder is deprecated in favour of directly using mplayer now.

---

### Post by CoximusPrime on 2012-04-26
> **BicyclerBoy said:**
> I have a suspicion that the video frame sizes need to be multiples of 8 or 16 depending on the codec etc.

The swscaler routines might not like 306. Try 312 or 304 (16*19).

I think mencoder is deprecated in favour of directly using mplayer now.

You are a genius!!! :)

I have altered the script to scale to "scale=-2:304" and it now works ... though the calculated width is 716, which is not a multiple of 8. Am I correct in therefore assuming that the swscaler routine does not require a width which is a multiple of 8, but it does require this for the height?

Many thanks for your help on that, my computer was getting closer and closer to going out of the window earlier! :)

---

### Post by BicyclerBoy on 2012-04-26
Not sure but..I would guess that the width is being padded to multiples of 8 or 16, this is commonly done.
Maybe the mencoder code is expected to be scaled to a height value & it then tweaks the width.

Video codec require multiple of 8 & 16 for efficient encoding both in final PQ & computional speed.

---

