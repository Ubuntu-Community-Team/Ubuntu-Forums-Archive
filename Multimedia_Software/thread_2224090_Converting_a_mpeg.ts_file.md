---
title: "Converting a mpeg.ts file"
date: 2014-05-14
forum: Multimedia Software
---

### Post by olliemonster on 2014-05-14
I have a pvr built into my telly that records tv shows in the mpeg transport stream that has a file extension of .ts i currently convert it though avidemux and than edit it though openshot. However I wanted to know if they was a easier way to do that or a way to do it with multiple files in a queue? It's realy annoying me. ](*,)

In case it helps my hardware is
A quad core amd a10 cpu
7.0 GiB of ram
The graphics card is an AMD Radeon HD 7660D
Thanks Oliver

---

### Post by HiImTye on 2014-05-14
you can use ffmpeg
```
sudo apt-get install ffmpeg
```
go to the folder you want to convert them in and
```
for f in *.ts; do ffmpeg -i "$f" "${f%.*}.ts; done
```

---

### Post by olliemonster on 2014-05-15
Thanks hilmtye

are there any other ways

---

### Post by HiImTye on 2014-05-15
there's [AutoFF](http://forum.videohelp.com/threads/289846-AutoFF-a-new-gui-for-FFmpeg-%28v-0-99-8%29) but I've never used it as I prefer the command line

---

### Post by mdalacu on 2014-05-16
Or, you can try my app.
[http://dmsimpleapps.blogspot.com/2014/04/dmmediaconverter.html](http://dmsimpleapps.blogspot.com/2014/04/dmmediaconverter.html)

---

### Post by olliemonster on 2014-05-16
Thanks guys i think ill mark this as solved now

---

### Post by MartyBuntu on 2014-05-16
You'll probably have to demux the audio, though...
Transport Stream captures tend to lose audio sync otherwise.

---

