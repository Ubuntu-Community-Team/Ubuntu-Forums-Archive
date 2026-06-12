---
title: "Convert Avi to Flv or SWF"
date: 2008-03-11
forum: Multimedia &amp; Video
---

### Post by Das Oracle on 2008-03-11
I have tried using ffmpeg and winff to convert avi files to flv however I am not getting any audio, is there something that I am missing or not doing?

for ffmpeg i am using:

```
ffmpeg -i myavifile.avi myflvfile.flv
```

---

### Post by BCtom on 2008-03-24
I think the best thing to do is look at the ffmpeg document web page and see what specific commands you need for your type of audio codec used in your video.avi file. I know from my experience with DIVX movies, lame-mp3 audio is used a lot and I need to indicate the bit rate for that codec. So depending on what type of avi file it is, the straight conversion to swf or flv my not be enough as is?

[ http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html]("http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html")

I hope this is helpful?

---

