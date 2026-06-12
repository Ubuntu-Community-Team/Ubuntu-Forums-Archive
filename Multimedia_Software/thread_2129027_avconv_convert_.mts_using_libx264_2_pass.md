---
title: "avconv convert .mts using libx264 2 pass"
date: 2013-03-25
forum: Multimedia Software
---

### Post by elempe on 2013-03-25
I know there are similar questions around, but unfortunately didn't find answer to my question. 
What I like to achieve is video camera originated videos compress as small as possible with as less as possible quality loss. And resize video from 1080p to 720p (720i).
So to get best result it is advisable to use 2 pass encoding. At this problem I have a problem. When I run 2nd pass I get error:


```
[libx264 @ 0xd9b8a0] constant rate-factor is incompatible with 2pass.
```

I have tried very different configurations, but unfortunately didn't find where is my mistake.
For example:

```
avconv -y -i 00000.MTS -qscale 3 -vcodec libx264 -preset medium -pass 1 -f mp4 /dev/null
avconv -y -i 00000.MTS -qscale 3 -vcodec libx264 -preset medium -pass 2 test.mp4
```
there is no resize or other tags, just to make it as simple as possible.
I'd be happy if someone could advise how to achieve my goal, or at least point to my mistake ;)


Thanks!

---

### Post by andrew.46 on 2013-03-25
Single pass crf encoding might very well be enough:

```
avconv -y -i 00000.MTS -crf 20 -vcodec libx264 -preset medium test.mp4
```

And add in a filter to resize...

---

### Post by elempe on 2013-03-25
> **andrew.46 said:**
> Single pass crf encoding might very well be enough:
...


Thanks andrew.46 for your answer. 
Single pass encoding works very well indeed.
I'm not a even close to video pro, but I have read a bit about converting videos, and if I have understood correctly, 2 pass (or even more than 2 passes) encoding is right way to get  best video quality in as small as possible file ;)

---

### Post by evilsoup on 2013-03-25
Read [this](http://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide).

The ffmpeg wiki is generally a pretty good resource.

---

