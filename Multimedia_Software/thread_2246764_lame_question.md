---
title: "lame question"
date: 2014-10-03
forum: Multimedia Software
---

### Post by yulie on 2014-10-03
Hello, i hope someone can help me-
I would like to convert wav-files to mp3 with** for i in *.wav; do lame  -V4  "$i" "`basename "$i" .wav`".mp3; done **

and provide a tracknumber to the mp3-file (the wav doesn't have one), so that the output is 1.mp3, 2.mp3 and so on.

I can't find out if and how it works..

Does someone know? Thanks!

---

### Post by kc1di on 2014-10-03
[this answer]("http://askubuntu.com/questions/59520/how-to-convert-wav-to-ogg-and-mp3-using-vbr") may be of help to you.
good luck.

---

### Post by yulie on 2014-10-03
I tried to add --tn : **... do lame -V 5 --add-id3v2 --pad-id3v2 --ignore-tag-errors --tn track   "$i" "`basename "$i" .wav`".mp3;** done, but it did not add a number to the output..

---

