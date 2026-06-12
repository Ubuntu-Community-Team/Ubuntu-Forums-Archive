---
title: "FAAC produces m4b files with odd lengths"
date: 2009-02-06
forum: Multimedia Software
---

### Post by blueridgedog on 2009-02-06
When I make an m4b file using FAAC, then import them to my iPod with Floola, the length of the file is wrong by many many many orders of magnatude (a 7 hour long audio book will display in the iPod as being 110000 hours long, so the progress bar never moves during replay).

I make the file with:

```
nice -10 madplay -q -o wave:- "$outputfile" | nice -10 faac -w --artist "${ARTIST}" --title "${TITLE}" --album "${ALBUM}" --year "${YEAR}" --genre "Speech" --track "01" -q 80 -o "$m4bname"
```

The variables are set via a script.

---

### Post by cesera on 2009-02-15
I normally make m4b files with the following command with good results:
 
```
mpg123 -s */*.mp3 | faac -b 80 -P -X -w -o $1.m4b -
```
 
I don't use all the variables, but do use the -P and -X options (can't remember why, but found it somewhere on the internet).
 
 
Hope this helps.

---

