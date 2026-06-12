---
title: "trying to convert to mp3 with ffmpeg on oneiric ..."
date: 2011-12-11
forum: Multimedia Software
---

### Post by shantiq on 2011-12-11
New install of Oneiric with ffmpeg



trying to convert to mp3 and getting


```
  Stream #0.0 -> #0.0
Encoder (codec id 86017) not found for output stream #0.0
```



what am i missing?   got Lame so far

my ffmpeg is 

ffmpeg version 0.7.2-4:0.7.2-1ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Oct  2 2011 15:13:26 with gcc 4.6.1

---

### Post by shantiq on 2011-12-11
sorry my mistake


had forgotten to enter ```
-acodec libmp3lame
```


in the line  ```
for f in *; do ffmpeg -i "$f" -ab 192k -acodec libmp3lame "${f%.*}.mp3"; done 
```


pretty sure it worked without it before must be a different version of ffmpeg; anyway   sorted:KS

---

