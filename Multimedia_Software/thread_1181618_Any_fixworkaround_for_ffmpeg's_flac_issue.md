---
title: "Any fix/workaround for ffmpeg's flac issue"
date: 2009-06-08
forum: Multimedia Software
---

### Post by Jethro_uk on 2009-06-08
After hours of fiddling around with Amarok, trying to copy some flac files to my MP3 phone, I discoved the transcode script, which uses ffmeg won't work, as ffmeg has a bug converting flac files.

Does anyone know of a work around, or do I have to use Windows Media Player to copy music to my walkman ?

---

### Post by mc4man on 2009-06-08
you might want to post your script and ffmpeg version. 

i use a very simple one that's works fine without ffmpeg. the blue can be whatever or where ever you wish (lame options, destination folder name, ect.

```
#!/bin/bash
for f in *.flac
do
OUTF=`echo "$f" | sed s/\.flac$/.mp3/g`

ARTIST=`metaflac "$f" --show-tag=ARTIST | sed s/.*=//g`
TITLE=`metaflac "$f" --show-tag=TITLE | sed s/.*=//g`
ALBUM=`metaflac "$f" --show-tag=ALBUM | sed s/.*=//g`
GENRE=`metaflac "$f" --show-tag=GENRE | sed s/.*=//g`
TRACKNUMBER=`metaflac "$f" --show-tag=TRACKNUMBER | sed s/.*=//g`
DATE=`metaflac "$f" --show-tag=DATE | sed s/.*=//g`

flac -c -d "$f" - | lame [COLOR="Blue"]-q 0 --vbr-new -V 2[/COLOR]   - "$OUTF"
id3v2 -t "$TITLE" -T "${TRACKNUMBER:-0}" -a "$ARTIST" -A "$ALBUM" -y "$DATE" -g "${GENRE:-12}" "$OUTF"
done
mkdir [COLOR="Blue"]"$ALBUM"[/COLOR]
mv *.mp3 [COLOR="Blue"]./"$ALBUM"[/COLOR]

```

Requires having  id3v2 for tagging

---

### Post by Jethro_uk on 2009-06-08
Thanks for that, I will post the details you requested when I am at homek, and booted into Ubuntu ...

---

