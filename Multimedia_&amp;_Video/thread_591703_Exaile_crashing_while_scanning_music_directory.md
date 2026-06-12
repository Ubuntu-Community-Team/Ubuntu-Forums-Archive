---
title: "Exaile crashing while scanning music directory"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by gtrtx on 2007-10-25
Hello,
I have an issue with exaile crashing when I tried to re-scan my music directory. 

It seems to work the first time I start it, but any re-scans cause it to crash. 

when running from a terminal I get the following each time: 

-----------------------
 read_from_path ( /usr/lib/exaile/xl/media/__init__.py @ 541):
-----------------------
Traceback (most recent call last):
  File "/usr/lib/exaile/xl/media/__init__.py", line 558, in read_from_path
    formats[ext].fill_tag_from_path(tr)
  File "/usr/lib/exaile/xl/media/ogg.py", line 42, in fill_tag_from_path
    f = mutagen.oggvorbis.OggVorbis(tr.io_loc)
  File "/usr/lib/exaile/xl/media/__init__.py", line 402, in get_loc_for_io
    return self._loc.encode(xlmisc.get_default_encoding())
UnicodeDecodeError: 'utf8' codec can't decode bytes in position 63-66: invalid data

Segmentation fault (core dumped)

---------------

at this time I'm running the latest 64bit version from the Exaile website, this also occurs when I use exaile from the ubuntu repos.

Any help or info would be appreciated. 

thanks.

---

