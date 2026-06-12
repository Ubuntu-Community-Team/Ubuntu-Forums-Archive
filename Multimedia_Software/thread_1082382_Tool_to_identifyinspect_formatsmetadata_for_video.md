---
title: "Tool to identify/inspect formats/metadata for video"
date: 2009-02-27
forum: Multimedia Software
---

### Post by yang on 2009-02-27
Are there any tools (or even straightforward libraries for e.g. Python) for identifying a video's formats (containers, tracks, encodings, variants, etc. - as many details as can be spared) and its metadata (size, ratio, duration, etc.)?  `file` is a start, but it provides only minimal information.  Thanks in advance!

(FWIW, on Windows, the only FOSS I've found for this are Gspot and Avicodec.)

---

### Post by mc4man on 2009-02-27
mediainfo can present some decent info, the view -> HTML gives more info than 'easy'

[http://www.getdeb.net/search.php?keywords=mediainfo](http://www.getdeb.net/search.php?keywords=mediainfo)
(for intrepid i386. hardy and amd_64 versions available.

Requires 2 packages, install them from right to left or dl all 3 to a folder and do a sudo dpkg -i *.deb

('drag and drop' on mediainfo window is easier than browse

---

