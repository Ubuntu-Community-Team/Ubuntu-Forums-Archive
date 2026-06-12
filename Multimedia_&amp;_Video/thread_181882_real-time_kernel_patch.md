---
title: "real-time kernel patch"
date: 2006-05-24
forum: Multimedia &amp; Video
---

### Post by stbub on 2006-05-24
Out of curiosity,

Anyone knows why the real-time patch hasn't made it in the official kernel yet?

I must say I'm VERY impressed with ardour/jack even without the rt patch.  I've known about this software for a while, but only recently gave it a try.

(Of course, when I start using QSynth, my Athlon 2200 is not overly happy :-))

---

### Post by dolson on 2006-05-26
It is a HUGE patch. It is very invasive. Any time you make changes to code, you introduce potential for new bugs. And since mainline kernel developers aren't all musicians or realtime users, they aren't in a huge rush to introduce a huge patch like this, although I think small bits might make it into the kernel. Besides, the patch changes every couple days, so it's not even stable yet.

---

