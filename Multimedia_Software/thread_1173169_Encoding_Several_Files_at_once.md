---
title: "Encoding Several Files at once?"
date: 2009-05-29
forum: Multimedia Software
---

### Post by pepperedeggs on 2009-05-29
I have just started using Ubuntu after wanting to stuff my copy of WinXP up mr.gates anus. I have found the transistion fairly smooth as I had dabbled in linux years ago and my current project is encoding or converting. 

I am using ffmpeg to convert several avi files to wmv and have about  400-500 left to do :-/ Doing this one by one is slightly annoying. 

Now I know I can que many up in the GUI but I prefer using terminal as I get better control on keeping the quality as that seems to degrade slightly after conversion. But does anyone know how to que up several files for conversion via terminal?

---

### Post by FakeOutdoorsman on 2009-05-29
Read through the [Linux Basics: A gentle introduction to 'find' guide](http://ubuntuforums.org/showthread.php?t=1128937).  Using that guide, I came up with:
```
find $HOME -name '*.avi' -type f -print | xargs -I '{}' ffmpeg -i '{}' '{}.wmv'
```
Also, why do you want to use WMV?

---

### Post by Keith Hedger on 2009-05-29
I have just re-encoded all my music and wrote this script```
#! /bin/bash

find -iname "*.flac" | while read
	do
	DIR=$(dirname "$REPLY")
	FILENAME=$(basename "$REPLY" .flac)
	OUTNAME="${DIR}/${FILENAME}.m4a"
	ffmpeg -i "$REPLY" "$OUTNAME" 0</dev/null
#	rm "$REPLY"
done
```

just change the suffixes to whatever you want and uncomment the 'rm' line if you want the original files removed.

---

