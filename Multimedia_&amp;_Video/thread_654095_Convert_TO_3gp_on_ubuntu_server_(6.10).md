---
title: "Convert TO 3gp on ubuntu server (6.10)"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by maqen on 2007-12-30
Hi...

Have been looking for a solution for alot of hours now... Having problems trying to convert a .avi file to .3gp file on ubuntu server (6.10) with ffmpeg...

ffmpeg -i video_clip.avi -s qcif -vcodec h263 -acodec mp3 -ac 1 -ar 8000 -r 25 -ab 32 -y clip.3gp

returning a unknown format for input (avi)

ffmpeg -i video_clip.mpg -s qcif -vcodec h263 -acodec mp3 -ac 1 -ar 8000 -ab 32 -y clip.3gp

returns unsupported codec for output stream

Was trying install ffmepg from medibuntu repo but dont really know how to do it...

Any one with ideas?

Cheers

---

