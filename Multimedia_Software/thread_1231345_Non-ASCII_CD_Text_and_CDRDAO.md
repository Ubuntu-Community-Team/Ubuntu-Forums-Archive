---
title: "Non-ASCII CD Text and CDRDAO"
date: 2009-08-04
forum: Multimedia Software
---

### Post by Michael.28 on 2009-08-04
Is it possible to burn CDs with CD-Text with non-ASCII characters using
cdrdao?

As far I know, CD-Text has to be encoded as iso-8859-1 (or us-ASCII).
However, cdrdao does not seem to be able to read a cdrdao TOC file encoded
in the iso-8859-1 character-set: I get "cannot find file:
[nonasciifilename.wav]" errors when it looks for the WAV files.

Cdrdao can read the same TOC file if it has been converted to utf-8, but
then cd-text on the burned CD is garbled and/or non-ASCII chars are fudged
(Swedish å comes out as Ã¥, for example) -- presumably because the CD-Text
needs to be in iso-8859-1 compatible format...

Additional info: I am generating the cdrdao TOC files by converting Exact
Audio Copy CUE files using mktoc.  Most of my audio files have names with
non-ASCII characters - like o with umlauts over it.

Any help appreciated!
_________________________
System info: Debian Lenny; K3B 1.0.5; cdrdao 1.2.2

---

