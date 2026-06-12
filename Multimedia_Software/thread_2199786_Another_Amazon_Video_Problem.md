---
title: "Another Amazon Video Problem"
date: 2014-01-15
forum: Multimedia Software
---

### Post by MarkID on 2014-01-15
Amazon videos played fine in Firefox this afternoon.  (I don't bother with watching Amazon videos in Chrome/Chromium.)  Tonight it doesn't work.  I tried the usual -- HAL, uninstalling Gnash, disabling Pepper.  Nothing works.  Please advise.

---

### Post by SeijiSensei on 2014-01-16
Using the "pipelight" solution for Silverlight DRM worked for me.  See: [http://ubuntuforums.org/showthread.php?t=2197798](http://ubuntuforums.org/showthread.php?t=2197798).

---

### Post by MarkID on 2014-01-16
Good idea.  Tried it.  Other Silverlight sites now work.  Amazon Prime still not.  In truth, Amazon was working today (before Pipelight).  Then stopped.  Installed Pipelight.  Still no Amazon Prime.

---

### Post by SeijiSensei on 2014-01-17
Do you still have hal and libhal1 installed?  Try removing them.  As I wrote in the other thread, I added pipelight to a system without either of those installed, and I could view Prime content.

---

