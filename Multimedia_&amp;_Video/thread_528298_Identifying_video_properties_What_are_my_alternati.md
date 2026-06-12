---
title: "Identifying video properties: What are my alternatives?"
date: 2007-08-17
forum: Multimedia &amp; Video
---

### Post by kwaanens on 2007-08-17
I'm looking for alternative commands for identifying the properties for individual video-files. By properties, I mean framerate, codecs used, audio/video bitrate, etc.

So far, I've found:
idvid (from package Tovid, see getdeb for deb)
exiftool (from package libimage-exiftool-perl)

What others are there? So far, exiftool looks to be the best, but it doesn't give video framerate :-(

- Ketil

---

### Post by darkkith on 2008-01-17
old topic ..  but..

this is a shell script i use to identify video files, relies on mplayer

```
#!/bin/sh
mplayer -vo null -ao null -frames 0 -identify "$@" 2>/dev/null |
        grep "^ID" |
        sed -e 's/[`\\!$"]/\\&/g' |
        sed -e '/^ID_FILENAME/ { s/^ID_FILENAME=\(.*\)/ID_FILENAME="\1"/g; }'
```

---

### Post by kwaanens on 2008-01-17
Cool! Thanks! I'll try it out.

---

