---
title: "DVD editing"
date: 2007-02-18
forum: Multimedia &amp; Video
---

### Post by vtec on 2007-02-18
I have a DVD that I recored with a video camera that I would like to remaster. All I need to do is cut our a small part and add some titles. I tired using Kino, but it does not seem to be able to import DVD video, only DV. Is there a better program for this??? Can Kino do this, and I'm just missing it???

---

### Post by rlgc79 on 2007-02-19
EDIT:
Try Acidrip to copy the DVD to a single file (copy video and audio, no re-encoding). 

Then use ffmpeg to convert the resulting file to a DV file.
ffmpeg -i <filename> -target ntsc-dv  final.avi

Kino should do the job then.


You could also try to use Cinelerra. Probably you have to compile from the source, but it is not difficult (there are some how-tos on the forum). Cinelerra is a powerful program, but not so easy for beginners...

Hope it helps,
Cheers

---

