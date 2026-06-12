---
title: "avi tags"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by davebridges on 2008-03-01
Does anyone know of software for editing meta data in avi files.  maybe even something to insert an image as a thumbnail as well.  thanks

---

### Post by linuxisfree on 2008-06-27
Honestly Dave, i'm trying to find the same thing, but i still haven't found anything... so anyone else?

---

### Post by MonkeeSage on 2008-07-06
The avi header length is limited, so inserting an image is probably not going to work (more advanced formats like matroska and ogg allow for binary metadata blobs I believe).

From my past twiddling with ffmpeg, it seems that the -title, -author, and -comment command-line switches correspond to the "tombstone" header fields INAM, IART and ICMT in a RIFF/AVI.

So something like the following will re-tag an avi file:

```
ffmpeg -title "A title" \
  -author "Somebody" \
  -comment "www.somewhere.com" \
  -acodec copy -vcodec copy \
  -i original.avi new.avi \
  && mv new.avi original.avi
```


Make backups first, of course. :)

---

