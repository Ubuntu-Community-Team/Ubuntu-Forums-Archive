---
title: "Problem with oggvorbis and exaile"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by HwH on 2007-04-24
I have install exaile on my dapper drake, whenever i try starting it up i get this error in terminal:
> GTK Accessibility Module initialized
Traceback (most recent call last):
  File "/usr/bin/exaile", line 61, in ?
    from xl import *
  File "/usr/share/exaile/xl/tracks.py", line 18, in ?
    import common, media, db, config, trackslist
  File "/usr/share/exaile/xl/media.py", line 19, in ?
    import mutagen, mutagen.id3, mutagen.flac, mutagen.oggvorbis
ImportError: No module named oggvorbis

has anyone else had this problem or knows how i can solve it?

thanks for any help in advance

---

