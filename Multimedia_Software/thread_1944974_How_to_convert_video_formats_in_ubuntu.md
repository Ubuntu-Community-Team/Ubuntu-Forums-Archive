---
title: "How to convert video formats in ubuntu"
date: 2012-03-22
forum: Multimedia Software
---

### Post by fayazali on 2012-03-22
Hi,
Can any body tell me that how to convert wmv video formats to avi,flv or in an other format in ubuntu please.

---

### Post by Bleastboy on 2012-03-22
use transmageddon video transcoder from software center or WinFF.
Hopes that helps

---

### Post by fayazali on 2012-03-22
> **Bleastboy said:**
> use transmageddon video transcoder from software center or WinFF.
Hopes that helps
Thanks , I think this works on GUI but i need a tool that should work on CLI interface(terminal) . That tool and procedure for using that will be appreciated.

---

### Post by howefield on 2012-03-22
Have you looked at ffmpeg ?

[http://ffmpeg.org/](http://ffmpeg.org/)
[http://ffmpeg.org/documentation.html](http://ffmpeg.org/documentation.html)

---

### Post by shantiq on 2012-03-22
```
mencoder -oac pcm -ovc copy -o sample.flv    sample.wmv
```


```
mencoder -oac pcm -ovc copy -o sample.avi   sample.wmv
```

---

