---
title: "subptools usage"
date: 2012-09-29
forum: Multimedia Software
---

### Post by bununtu on 2012-09-29
Greetings. I have been struggling with a movie and it's subtitles lately as I usually am able to find srt's for them. But this particular movie only has idx and sub files. I am able to get the xml output using the command sub2pgm, but I have been stumped from this point on. I have tried subptools command just about every which way to no avail. And performing a google search only comes up with the command page itself. Can someone please enlighten me on the correct usage of this command? Perhaps with some real-world examples. It would be greatly appreciated! Thanks...

---

### Post by vanadium on 2013-03-19
Ressurrecting an old, unanswered thread. Strungling with the same problem.

---

### Post by vanadium on 2013-03-19
In case someone, apart from the OP, cares, this is how you can convert vobsub subtitles to a text based srt format inder linux.

When you extracted the subtitles from a DVD, you end up with two files, with idx and sub extensions, for example basename.idx and basename.srt.

subp2pgm extracts the image subtitles into individual graphic files, one for each subtitle and an xml file describing the subtitles. Thus, the command
```

subp2pgm basename

```
produces a file basename.xml and many small numbered pgm graphics files.

The graphics files must now be ocr'd to readable text.
```

for f in *.pgm ;  do tesseract "$f" "$f" ; done

```
For each of the graphics, tesseract will produce a text file with the name of the graphics file and the .txt extension added.

subptools now can combine the text files into an srt subtitle, using the information in the xml file produced before:
```

subptools --convert srt -i basename.xml -o basename.srt -s

```

This yielded a good quality OCR for me in less than a minute (quite fast computer though). I thought to post it here, because I also have been looking for some way to do this on linux in vain.

---

### Post by pt123 on 2013-06-09
I found a pretty awesome tool vobSub2SRT, which has a ubuntu PPA also.
[https://github.com/ruediger/VobSub2SRT](https://github.com/ruediger/VobSub2SRT)

It converts .idx / .sub subtitles into .srt text subtitles by using Tesseract as OCR.

---

