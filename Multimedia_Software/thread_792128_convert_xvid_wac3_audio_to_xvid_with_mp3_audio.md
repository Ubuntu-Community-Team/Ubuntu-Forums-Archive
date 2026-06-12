---
title: "convert xvid w/ac3 audio to xvid with mp3 audio?"
date: 2008-05-12
forum: Multimedia Software
---

### Post by dustintinsley on 2008-05-12
ok, i am in need of help.  i use fuppes to stream/transcode my xvids to my xbox 360, but it does not like xvids with ac3 audio.  how can i convert these to mp3 audio xvids?  i have tried using avidemux, but have sync issues.  would like to use mencoder if possible, but i am not to familar with it.  any suggestions are welcomed...

---

### Post by dustintinsley on 2008-05-13
bump...

---

### Post by jocheem67 on 2008-05-14
Well: the trick using mencoder would be to do a copy of the video -ovc copy and do a -oac mp3lame -lameopts vbr=3 -o /dev/null
( or something like that ).
Check on the mencoder official site, it's covered extensively...

[http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#menc-feat-dvd-mpeg4-codec](http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#menc-feat-dvd-mpeg4-codec)

My expreiences are that keeping stuff synchronised is a hard thing using mencoder. Here too however there's documentation.

---

