---
title: "Flac files"
date: 2010-12-07
forum: Multimedia Software
---

### Post by jajapop on 2010-12-07
Hi, I downloaded some flac files (15 cd's) and When i wanted to change them to mp3's there's something wrong with the log file that vlc will read them like songs but max will just read one long song. Anyone know if i can make it an iso or something and then convert it to individual (songs) mp3's.

thanks in advance, i hope I was clear, 

j

---

### Post by AlphaLexman on 2010-12-07
Here is my favorite script to convert *.flac to *.mp3:
```
#!/bin/bash

## this script works in a single dir!

for a in *.flac

do
OUTF=`echo "$a" | sed s/\.flac$/.mp3/g`

ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`
DATE=`metaflac "$a" --show-tag=DATE | sed s/.*=//g`

if [ ! -e "$OUTF" ]; then
	flac -c -d "$a" | lame -m j -q 0 --vbr-new -V 0 -s 44.1 - "$OUTF"
fi
id3v2 -t "$TITLE" -T "${TRACKNUMBER:-0}" -a "$ARTIST" -A "$ALBUM" -y "$DATE" -g "${GENRE:-12}" "$OUTF"

done 
```

---

