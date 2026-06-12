---
title: "Graphic applications have started to crash (in Feisty)"
date: 2007-10-19
forum: Multimedia Production
---

### Post by jis on 2007-10-19
Krita crashes at beginning (and causes signal 11). Cinepaint crashes at preferences dialog. I think they worked better before.

I have Krita (1:1.6.3-0ubuntu1~feisty1) and Cinepaint (0.22-1-0ubuntu~feisty1) installed from feisty-backports. Is there any chance that  they work better in Gutsy even if they have the same (base) version number?

Anybody else have these problems?

BTW. I wish they include cinepaint-ufraw in ubuntu (cinepaint plugin) 
or at least put it in getdeb.net (although I am not yet confident with the quality of ufraw with my dng files).

---

### Post by jis on 2007-10-19
I tested with regular Feisty version of Cinepaint and same thing. I had added a ICC profile directory that is under my home directory in preferences and since that it would crash, if I reopen the dialog. Removing the directory entry in ~/.cinepaint/gimprc stops the behavior. Very odd bug.

---

