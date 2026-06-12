---
title: "Does anyone know  how to make a screencast?"
date: 2008-07-20
forum: Multimedia Software
---

### Post by Oscar Pradilla on 2008-07-20
I i want to  make a screencast with ubuntu, what program should i use?

Tks.

---

### Post by goldsniper on 2008-07-20
gtk record my desktop. I'm trying it right now but still figuring out how to convert  those ogv file into flv file.

---

### Post by goldsniper on 2008-07-20
I think this links should help us.

[http://ubuntuforums.org/showthread.php?t=479953&highlight=screencast]("http://ubuntuforums.org/showthread.php?t=479953&highlight=screencast")

---

### Post by Creative2 on 2008-07-20
rename that files as recording.ogg
then 

mencoder  INPUT.ogg -oac lavc -ovc lavc -of lavf -lavcopts vcodec=flv:vbitrate=700:acodec=libmp3lame:abitrate=128 -ofps 30 -srate 44100  -o OUTPUT.flv

you can of course use fuoco tools.. or winff or or or ..

---

