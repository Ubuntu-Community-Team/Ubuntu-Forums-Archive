---
title: "Kdenlive -&gt; youtube audio codec problem"
date: 2010-06-09
forum: Multimedia Software
---

### Post by yours-truly on 2010-06-09
Moin moin,

Ich versuche nun schon seit Stunden aus Kdenlive heraus zu exportieren, um anschließend, das Video, bei YouTube hochzuladen.
Der Audio Codec konnte nicht erkannt werden, die Konvertierung bei YouTube ist fehlgeschlagen.
Vimeo hat mit meinen Videos keine Probleme.

Ausprobiert habe ich ->
acodec=libfaac ab=128k ar=44100
acodec=mp3lame ab=128k ar=44100 
acodec=libmp3lame ab=128k ar=44100 

Keinen davon mochte er.
Tausend Dank im Vorhinein für jeden nützlichen Tip.

Mit vernetzten Grüßen,
yours truly

Edit: Sorry, I forgot, this is an english Board. 

I'm trying to upload a video export from kdenlive.
youtube is telling me, the audio codec isn't correct,
but as you can see above, i doesn't matter which codec I use.

Thank you for any usefull tips on how to solve this problem.

yours truly

---

### Post by Jinger on 2010-06-09
[Here]("http://www.google.com/support/youtube/bin/answer.py?hl=en&answer=132460") You can find everything you want.

---

### Post by yours-truly on 2010-06-18
Sorry to say,
thats no help at all.

And of course, I've looked at this page more than twice to doublecheck if I missed an important hint.

For all those who might have an equal Problem:
Export your Movie as flash, this is was for me
a first workaround to get things done.

ciao 
yt

---

### Post by yours-truly on 2010-06-23
Another accepted Export Format for YouTube and Vimeo:

Use this as Userdefined profil

f=mpegts acodec=mp2 ab=384k ar=48000 ac=2 vcodec=mpeg2video s=1920x1080 b=25000k g=12 trellis=1 profile=hdv_1080_25p

Thanks, and problem solved.
yours truly

---

