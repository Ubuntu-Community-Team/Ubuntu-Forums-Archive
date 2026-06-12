---
title: "How to convert *.cue + single *.mp3     to several *.mp3 for amarok?"
date: 2008-12-25
forum: Multimedia Software
---

### Post by frenchn00b on 2008-12-25
Hello,

Since Amarok has NO support for CUE files, how can we convert the album into separated mp3?

album.cue
album.mp3

Thanks

---

### Post by frenchn00b on 2008-12-26
bump

with adding the right tags in the mp3 (so that the mp3 is nicely built from the cue)

---

### Post by frenchn00b on 2008-12-26
Here there is a patch:
[http://markmail.org/message/acccffjxqozzbaxj](http://markmail.org/message/acccffjxqozzbaxj)

can someone make a deb or tar.gz ... for amarok?

---

### Post by frenchn00b on 2008-12-26
In progress ... 

```
amarok-1.4.4$ patch -p1 < cuefile.diff 
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Index: src/contextbrowser.h
|===================================================================
|--- src/contextbrowser.h       (Revision 418008)
|+++ src/contextbrowser.h       (Arbeitskopie)
--------------------------
File to patch: amarok/src/contextbrowser.h
patching file amarok/src/contextbrowser.h
Hunk #1 succeeded at 29 with fuzz 2 (offset 8 lines).
Hunk #2 FAILED at 148.
1 out of 2 hunks FAILED -- saving rejects to file amarok/src/contextbrowser.h.rej
can't find file to patch at input line 28
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|Index: src/contextbrowser.cpp
|===================================================================
|--- src/contextbrowser.cpp     (Revision 418008)
|+++ src/contextbrowser.cpp     (Arbeitskopie)
--------------------------
File to patch: amarok/src/contextbrowser.cpp
patching file amarok/src/contextbrowser.cpp
Hunk #1 succeeded at 34 with fuzz 2 (offset 9 lines).
Hunk #2 FAILED at 205.
Hunk #3 FAILED at 215.
Hunk #4 succeeded at 535 with fuzz 2 (offset 189 lines).
Hunk #5 FAILED at 613.
Hunk #6 FAILED at 667.
Hunk #7 FAILED at 713.
Hunk #8 succeeded at 2249 with fuzz 2 (offset 697 lines).
5 out of 8 hunks FAILED -- saving rejects to file amarok/src/contextbrowser.cpp.rej
```

---

