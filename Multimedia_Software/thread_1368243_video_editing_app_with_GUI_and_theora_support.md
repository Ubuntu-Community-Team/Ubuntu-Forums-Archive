---
title: "video editing app with GUI and theora support?"
date: 2009-12-30
forum: Multimedia Software
---

### Post by Lucas Malor on 2009-12-30
I'm searching for a visual video editing application that supports Theora (Avidemux doesn't).
A good FFMpeg / MEncoder frontend is a good alternative :)

---

### Post by cotcot on 2009-12-30
Theora is a free open format. Most linux video editors will be able to use it. Kdenlive, cinelerra, pitivi, openshot are some of them reporting ogg theora support.

---

### Post by Lucas Malor on 2010-01-04
Good. Kdenlive seems a good program. I found [on Wikipedia]("http://en.wikipedia.org/wiki/Comparison_of_video_editing_software") Blender, what do you think about?

---

### Post by Lucas Malor on 2011-07-04
Well, I found that the best way is to use ffmpeg:

```
ffmpeg -i INPUTFILE -f ogg -vcodec libtheora -acodec libvorbis -b 866000 -ab 80000 OUTPUTNAME.ogv
```

---

