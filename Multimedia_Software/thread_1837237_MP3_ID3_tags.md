---
title: "MP3 ID3 tags"
date: 2011-09-01
forum: Multimedia Software
---

### Post by steviefordi on 2011-09-01
I am using Banshee (2.01) to rip CD's to MP3 on my Ubuntu Lucid machine. The
tags are written as ID3v2.4, which are ignored by my player as it only reads
ID3v2.3.

I know this is probably a Gstreamer thing, but does anyone know how to write
the tags correctly for my player during the rip.

P.S. I know I can use tag editing software after ripping, but I don't want
to go through that extra step.

---

### Post by vijushimpi on 2011-09-01
Just if you change your mind -
```
sudo apt-get install eyeD3
cd yourmp3folder
eyeD3 --to-v2.3 *
```

---

### Post by steviefordi on 2011-09-01
Ok, it appears I may have to put a watch on my music folder and script that change you've entered for any .mp3 files.

Thanks for the reply.

---

