---
title: "flv ---&gt; mpeg4"
date: 2007-12-10
forum: Multimedia &amp; Video
---

### Post by Folk Theory on 2007-12-10
are there any programs that enable transforming video formats, especially .flv to mpeg4?

---

### Post by stooshbunutu on 2008-02-04
for .flv files there is a realy easy porgram  I use: [winff]("http://biggmatt.com/files/winff-0.33-i386.deb") that uses the [ffmpeg]("http://packages.ubuntu.com/gutsy/graphics/ffmpeg") codec to covert the file. I'm not sure about the .mpeg4 format but certainly the .mpeg is one of them

hope this helps you, it works great for me.:)

---

### Post by FakeOutdoorsman on 2008-02-07
I use ffmpeg to transcode many video formats.

Quick example:
```
ffmpeg -i inputfile.flv -acodec copy -vcodec mpeg4 outputfile.mp4
```

---

