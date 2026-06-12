---
title: "FFMPEG help (flv - MP3)"
date: 2010-03-14
forum: Multimedia Software
---

### Post by Robert Lutken on 2010-03-14
hi im trying to convert a .flv video to MP3 format using ffmpeg as far as i know this is the command
ffmpeg -i d.flv -sameq -acodec mp3 -f asf d.mp3
however i am not sure and need some help , i get a error saying 
"Unknown encoder 'mp3'"
can someone tell the the correct command 
thanks very much 
welshy_rob

---

### Post by mc4man on 2010-03-14
If your ffmpeg is capable then it's  - acodec libmp3lame

(otherwise see here
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

(what your trying to do with that command is a bit unclear, particularly if the .flv contains video which I assume all .flv does - ?

---

### Post by Robert Lutken on 2010-03-14
Thanks very much, it works fine =) :D

---

### Post by temenex on 2010-03-14
[http://code.google.com/p/sinthgunt/](http://code.google.com/p/sinthgunt/)

Sinthgunt is an easy to use gui for ffmpeg.  ;)

---

### Post by castalla on 2011-04-17
I've got a conversion problem with Sinthgunt.  The mpeg preset options are greyed out and message that my ffmpeg version doesn't support the mpeg format!!!

There's a ffmeg sinthgunt patch available - but I've no idea how to apply it - there are no instructions available.

Any help gratefully received.

---

### Post by bowto on 2011-04-19
You can use the online server [free youtube to mp3 converter]("http://www.freeyoutubetomp3converter.org") ([http://www.freeyoutubetomp3converter.org](http://www.freeyoutubetomp3converter.org)). It works well for me and you do it online

---

