---
title: "how do you add boarders to a video with ffmpeg"
date: 2012-05-19
forum: Multimedia Software
---

### Post by someitalian123 on 2012-05-19
I am using Winff, the ffmpeg front end, but every time it creates a dvd it changes the aspect ration of the video instead of adding boarders to preserver it. I tried creating a custom present 

```
-f dvd -target ntsc-dvd -r 23.976 -vf scale=720:380 -vf pad=720:480:0:50:black -aspect 16:9 -vb 8000k -g 12 -mbd rd -trellis 1 -flags +mv0 -cmp 0 -subcmp 2
```

But it just returns this error

```
[pad @ 0x856fee0] Input area 0:50:720:530 not within the padded area 0:0:720:480 or zero-sized

```

The original video size is 720x320. So it would have to be scaled to 720x380 and then given 50 pixel boarders on the top and the bottom right? What am I doing wrong?

---

