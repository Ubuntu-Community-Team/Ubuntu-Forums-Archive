---
title: "FFMPEG quality loss"
date: 2011-01-29
forum: Multimedia Software
---

### Post by YigalB on 2011-01-29
i try to split mpeg file using ffmpeg. The splitting itself works OK, but the quality is lower. What should I do in order to keep the same video quality?

The way I used ffmpeg:
```
ffmpeg -i in.mpeg -ss 00:00:00 -t 00:02:58 out.mpeg
```

---

### Post by YigalB on 2011-01-29
i think I can reply myself:
there is a flag -sameq that keeps origin quality.

I have no idea why isn't it a default.

---

### Post by ron999 on 2011-01-29
> **YigalB said:**
> 
there is a flag -sameq that keeps origin quality.

No.
Try this command instead:-
```
ffmpeg -i in.mpeg -ss 00:00:00 -t 00:02:58 -vcodec copy -acodec copy out.mpeg

```

---

### Post by InspiredIndividual on 2011-01-29
Thanks YigalB, I learned something new.

---

### Post by YigalB on 2011-01-29
> **ron999 said:**
> No.
Try this command instead:-
```
ffmpeg -i in.mpeg -ss 00:00:00 -t 00:02:58 -vcodec copy -acodec copy out.mpeg

```

I tried what Ron suggested. The output file is now a bit larger, and it plays nice on the Ubuntu machine.
But unlike my previous trial (with -sameq), this file wont play on Windows machine - I have no idea why, but it's a must for me to be able to play it across platforms.

Just to make sure: the source video can be played on Windows and Ubuntu.

---

### Post by InspiredIndividual on 2011-01-29
You could also try to find out where exactly the loss of quality occurs by comparing the output of
```
ffmpeg -i video.mpeg
```

If you discover that, say, the bitrate is 200kb/s instead of 600kb/s, you could try and set the bitrate manually by
```
ffmpeg -i in.mpeg -b 600k out.mpeg
```

---

### Post by vanadium on 2011-01-29
Try the option "-f mpegts"

---

