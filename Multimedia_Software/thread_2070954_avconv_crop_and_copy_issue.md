---
title: "avconv crop and copy issue"
date: 2012-10-14
forum: Multimedia Software
---

### Post by mannux on 2012-10-14
Hey there,

I'm not sure if it is actually an issue or not, but trying to crop the video (ogv) and leave the codecs intact simply failes:

avconv -i infile.ogv -vf crop:1280:1024:8:60 -codec copy outfile.ogv

leaving outfile exactly as the original ie. not cropped!? (Original size is 1680x1050, btw...)
Tried different position of parameters, but no luck.

Anybody can 'open my eyes' and point what could be wrong here?

Cheers,
M.

---

### Post by msundman on 2012-10-31
You do need to *re-encode* the video if you want to crop it, you can't just *copy* the stream like in your example.

---

