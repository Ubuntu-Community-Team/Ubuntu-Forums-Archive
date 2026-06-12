---
title: "Convert MP3 to WMA"
date: 2008-09-17
forum: Multimedia Software
---

### Post by daemon3 on 2008-09-17
I've seen a lot of posts online and on Ubuntu Forums about how to convert wma to mp3, but how do I convert mp3 to wma?  I know that on one install some time ago, I used pacpl, but that doesn't install anymore.  Help, please? :D

---

### Post by marcordenis on 2008-09-17
Well honestly I don't really know, but if it's only for one file, you can use this site: [http://www.media-convert.com]("http://www.media-convert.com")
It can convert from pretty much any format to any other format.

---

### Post by mc4man on 2008-09-17
You can  do it with ffmpeg (depending on ver. installed, repo ver. may not work

You would do something like this (presumes .mp3 in home directory

```
ffmpeg -i foo.mp3 -acodec wmav2 -ab 128k  foo.wma
```

for .wav

```
ffmpeg -i foo.wav -acodec wmav2 -ab 192k  foo.wma
```

Bitrate chosen is changeable

---

