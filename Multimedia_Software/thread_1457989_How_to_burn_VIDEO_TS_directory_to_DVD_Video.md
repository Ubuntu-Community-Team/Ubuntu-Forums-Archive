---
title: "How to burn VIDEO_TS directory to DVD Video"
date: 2010-04-19
forum: Multimedia Software
---

### Post by dubref on 2010-04-19
What would be easiest way to burn a DVD-Video disk, provided I already have AUDIO_TS and VIDEO_TS folders on my hard drive copied from source DVD?

I managed to burn one disk creating ISO from folders with K9copy, but since then I get a strange error "Directory already exists.
Please choose another location or rename the DVD title.", choosing continue on K9copy goes through the motions of creating an ISO but does not actually make one! (renaming unknown.iso to something else does not help... :( )

In any case, I figure, if I do not need to further compress VIDOE_TS, I should be able to use something simpler(less bug prone) than K9copy.

I assume there must be a way with Brasero, but I do not wish to create a DVD data disk, I want a format which even a really old standalone DVD player would play.

EDIT: Maybe there really is no difference between DVD Data and DVD Video besides directory names?

---

### Post by 2hot6ft2 on 2010-04-19
k3b
or if you want a full dvd authoring program try
QDVDAuthor
[http://qdvdauthor.sourceforge.net/](http://qdvdauthor.sourceforge.net/)

---

### Post by ron999 on 2010-04-19
..........

---

### Post by Mia1990 on 2010-04-19
tovid is a great dvd burning software install svn tovid from there web site it's great a lot more options take a look at it [here]("http://tovid.wikia.com/wiki/Tovid_Wiki") down at the bottom of the page it gives a link to instructions on how to install svn tovid.

---

### Post by ron999 on 2010-04-19
.....

---

### Post by dubref on 2010-04-20
Thank you everyone for suggestions!

Brasero did in fact work, that is I simply burned AUDIO_TS and VIDEO_TS directories onto root of a fresh DVD(Brasero did say it was burning a DVD data disk, but it plays just fine, still have to test it on some older standalone players though).

Downloaded latest tovid sources from svn and compiled(only thing extra needed was python-tk package).
Tovid looks good! 

Looks like tovid may help on my next project:

Downconverting 6GB VIDEO_TS directory down to ~4GB

---

### Post by Linuxforall on 2010-04-20
Use DVD Styler or newly released Bombono.

---

