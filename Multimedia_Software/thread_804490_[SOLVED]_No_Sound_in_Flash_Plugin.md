---
title: "[SOLVED] No Sound in Flash Plugin"
date: 2008-05-23
forum: Multimedia Software
---

### Post by ghindo on 2008-05-23
I am running Ubuntu 8.04 and I cannot get sound in any embedded Flash in Firefox whatsoever.  I've tried Firefox 3 Beta 5 and Firefox 2, but it doesn't work in either.  Sound works with the rest of my system (even things like other videos in Firefox), but Flash does not.  I tried reinstalling Flash, but to no avail.  Gnash doesn't suit my needs yet, otherwise I would use it.

Help please?

---

### Post by PmDematagoda on 2008-05-23
Install libflashsupport with:-
```
sudo apt-get install libflashsupport
```

That should help, but there is one drawback, and that is that Firefox is most likely to crash while playing Flash. To completely fix this you can install Flash Player 10 beta which fixes the sound issue.

---

### Post by huczek on 2008-05-23
thank u for the answer. will i still need the libflashsupport after beta flashplayer 10 installed?
[direct link to flash player 10]("http://labs.adobe.com/downloads/flashplayer10.html")
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by PmDematagoda on 2008-05-23
> **huczek said:**
> thank u for the answer. will i still need the libflashsupport after beta flashplayer 10 installed?
[direct link to flash player 10]("http://labs.adobe.com/downloads/flashplayer10.html")
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

No, in fact, flashpluginsupport will cause more problems for Flash 10 than solve them, remove both flashpluginsupport and any previous installation of Flash before installing Flash 10.

---

### Post by ghindo on 2008-05-24
> **PmDematagoda said:**
> To completely fix this you can install Flash Player 10 beta which fixes the sound issue.That did the trick!  Wasn't hard at all to install, either!

Thank you!

---

