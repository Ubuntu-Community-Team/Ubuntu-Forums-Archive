---
title: "Severe compression artifacts"
date: 2012-08-31
forum: Multimedia Software
---

### Post by Jursinoff on 2012-08-31
After updating Ubuntu from 10.04 Lucid Lynx to 12.04, I've noticed major compression artifacts on webcam video.


In this picture this may not seem such a big problem, but on 42" screen this looks awful. notice the borders of red label that says CITY and also the edges of the letters.
[IMG]http://i4.aijaa.com/b/00229/10814426.jpg[/IMG]


With Ubuntu 10.04 the label is shown without any artifacts or color mix-up.



How can this be fixed?

---

### Post by Jursinoff on 2012-09-05
Does anyone know how to change the mpeg compression quality?

---

### Post by coldraven on 2012-09-05
I made this note sometime ago and I cannot remember if I ever used it but you could try a search for "video4linux control panel".
I hope it helps.

Note:
Install v4l2ucp
it comes up in system , preferences as video4linux control panel

---

### Post by Jursinoff on 2012-09-07
That offers me a bunch of image adjusting tools, which are also accessible through guvcview. Still there is no option of adjusting the level of compression, which seems to be the problem.

Here is the same problem explained in first chapter:
[http://en.wikipedia.org/wiki/Compression_artifact](http://en.wikipedia.org/wiki/Compression_artifact)

do you know if there is a way to configure or manually change maybe the codecs (or whatever handles webcam stream packaging) configuration?

---

