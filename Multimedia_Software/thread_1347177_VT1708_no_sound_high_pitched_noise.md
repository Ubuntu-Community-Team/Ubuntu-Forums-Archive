---
title: "VT1708 no sound high pitched noise"
date: 2009-12-05
forum: Multimedia Software
---

### Post by StuartZ on 2009-12-05
I have a VIA HDA sound card VT1708 A that was producing a high pitch sound in the speakers.  It took me a lot of searching etc to solve the problem.  I'm posting this to hopefully help someone else.

I installed gnome-alsamixer:

sudo apt-get install gnome-alsamixer

Then I opened it up and enabled the 5.1

Presto, no more noise.

5-16-10 Edit
On **Lucid** I installed the gnome-alsamixer and muted the front speaker to take care of the noise.

---

### Post by Ryann on 2009-12-05
I had, presumably, the same high pitched noise (complete with buzzing as well), though I had sound along with it. I installed alsamixer and pulled all the bars to high and this got rid of the problem. Thanks for sharing.

---

