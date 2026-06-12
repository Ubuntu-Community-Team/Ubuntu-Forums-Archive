---
title: "FFmpeg w/ WinFF"
date: 2008-07-21
forum: Multimedia Software
---

### Post by MrWES on 2008-07-21
How do I make ffmpeg create a 700mb avi file from a vob file? I've tried using the -fs setting, which does give me the approximately file size of 700mb, but cuts the video short. I also tried setting the bitrate to negative 700000, still no luck.

```
-r 29.97 -vcodec xvid -vtag XVID -s 704x384 -aspect 16:9 -maxrate 1800k -b 1500k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -g 300 -acodec mp3 -ar 48000 -ab 128k -ac 2
```

Bill

---

### Post by MrWES on 2008-07-22
bump

---

