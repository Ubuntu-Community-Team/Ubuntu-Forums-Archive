---
title: "Encoding a Generic DV video to DivX in mencoder"
date: 2008-05-22
forum: Multimedia Software
---

### Post by NCLI on 2008-05-22
I've imported some generic DV files from my video camera. I'd like to convert it to a better(smaller) format, but ffmpeg crashes when I try:

[img]http://xs227.xs.to/xs227/08214/screenshot-1634.png[/img]

---

### Post by cor2y on 2008-05-22
Looks to me like ffmpeg cannot understand the input video codec CDVC which is the problem.
Where did your version of ffmpeg come from the official repos?
Either try to compile it yourself , try the medibuntu version (more media type/codec support), or mencoder.
Although CDVC should be supported in ffmpeg why it can't be read for converting is a bit weird.

---

### Post by NCLI on 2008-05-22
Ok, I tried compiling, now this **** happens:

[img]http://xs227.xs.to/xs227/08214/screenshot-2946.png[/img]

---

