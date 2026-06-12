---
title: "Format conversion using Lame in command line"
date: 2007-02-13
forum: Multimedia &amp; Video
---

### Post by amanita on 2007-02-13
Hi, If I I want to convert wav to mp3 I will type in terminal e.g. ```
lame -h --abr 128  sample.wav sample.mp3
```
what  I cannot figure out is:

1. How to convert all folders?

2. How to use wildcards - typing just *.mp3 doesn't work.

(Sound Converter freezes when converting mp3 to mp3 from higher to lower quality)

---

### Post by empthollow on 2008-02-24
this should would if you are converting multiple files
```
lame -h --abr *.wav
```
the files will be named filename.wav.mp3 and you will have to rename them but easytag might make that a bit easier and quicker.

---

