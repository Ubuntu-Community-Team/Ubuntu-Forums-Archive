---
title: "DVD Authoring Software"
date: 2008-02-14
forum: Multimedia &amp; Video
---

### Post by pengin on 2008-02-14
What is the fastest dvd burning software for avi and mpeg files. i hve tried devede & brasero etc and they are all way to slow with the fastest time burning a dvd was 4 hours after that it would take double or triple that time. This is kinda urgent

---

### Post by aeiah on 2008-02-14
you could try tovid. i dont know if it'll be quicker though. it depends on the specs of your computer, but with mine it takes less than an hour. i havent done it in ages though so i cant really remember.

amd64 X2 3800, 2gb ram. 32bit ubuntu

---

### Post by ron999 on 2008-02-14
Hi
I use tovid to author DVDs.
The time-consuming part is converting a file into DVD-compliant format.
It speeds things up using the ffmpeg option.

Like this (for PAL):-
**tovid -pal -ffmpeg -in filename.avi -out movie**
This uses the file filename.avi to create movie.mpg in the correct format.

Then after that use makexml command.
Then after that use makedvd command.
Then burn the disc.
This is where to learn about tovid:-[http://tovid.wikia.com/wiki/Main_Page]("http://tovid.wikia.com/wiki/Main_Page")
:cool::cool:

---

### Post by pengin on 2008-02-14
Ok i shall give it a go. i'll let you know if i have any problems

---

