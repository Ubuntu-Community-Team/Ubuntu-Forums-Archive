---
title: "compress all files in dir whit ffmpeg"
date: 2015-02-15
forum: Multimedia Software
---

### Post by phs2004 on 2015-02-15
Hi

I want to compress about 700 movie clips and doing that like this is going to take some time 

```
ffmpeg -i 20141017_152844.mp4 -vcodec libx264 -crf 26 -acodec libfdk_aac 20141017_152844.mp4.mp4 
```

Have tyed many many ways for *.mp4 but only get errors :(. Im geting out of space on google drive 99.8% full off 100gb next is 1 tb its to expensive :)

---

### Post by TheFu on 2015-02-15
You need a loop.

```
#!/bin/sh
#
# This is for really simple XVID conversion, use
#
for filename in "$@"; do
   IN=$filename
   nice ffmpeg -i "$IN" -sameq -f avi -vcodec mpeg4 -acodec copy "$IN-ffmpeg.avi" 
done
```

Oh - and this script only works properly for input filenames that do not contain spaces or strange characters. There are ways around that, but I find it easier to just not have any files with those issues.

Clearly, you'd swap your command for mine.  The quotes are absolutely critical, BTW.

---

### Post by phs2004 on 2015-02-16
Ok tanks. Dident know about loop options. [h=2][/h]

---

### Post by TheFu on 2015-02-16
bash is a full programming language. So is ksh, borne shell, zsh, ... there's a great, free, how-to called "the advanced bash scripting guide" which shows hundreds of examples.  It has been around for years. "ABSG linux" search will find it.  There are beginning guides too. Sometimes we all need to see these simple examples to make things clear.

---

