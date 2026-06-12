---
title: "How to convert a directory of AVI files to play on LG Viewty mobile"
date: 2010-01-16
forum: Multimedia Software
---

### Post by seldon77 on 2010-01-16
I often have a bunch of avi files in a directory that I want to convert to see on my viewty mobile. This code will create a new 'mobile' directory within the directory and convert each avi file to the LG Viewty format. The original files will remain untouched.

```
mkdir mobile; IFS=$'\n' ; for f in `ls -1 *.avi` ; do FILE=$(basename "$f" .avi) ; mencoder "$FILE.avi" -oac lavc -lavcopts acodec=libmp3lame:abitrate=64 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=350 -ffourcc DX50 -vf scale=400:240 -o "mobile/$FILE.avi"; rm "frameno.avi"; rm "divx2pass.log"; sleep 60; done
```

---

