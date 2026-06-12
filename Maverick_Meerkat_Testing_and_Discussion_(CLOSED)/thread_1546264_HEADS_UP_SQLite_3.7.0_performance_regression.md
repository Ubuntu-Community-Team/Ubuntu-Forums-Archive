---
title: "HEADS UP: SQLite 3.7.0 performance regression"
date: 2010-08-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by gnomeuser on 2010-08-05
Distributions around the globe have been upgrading SQLite to 3.7.0, however this version is plagued by some rather nasty performance regressions. 

In Banshee we noticed that sudden queries went from taking milliseconds to taking minutes. The same queries applied directly to sqlite experiences the same behavior.

As Maverick was updated, if you use anything that links to the system SQLite such as Banshee you can expect erratic performance. 

My personal recommendation would be to lock the version at 3.6.x till 3.7.1 is out and confirmed to fix the regressions.

Upstream "report":
[http://permalink.gmane.org/gmane.comp.db.sqlite.general/58588](http://permalink.gmane.org/gmane.comp.db.sqlite.general/58588)

Tracking bug for Ubuntu:
[https://bugs.launchpad.net/bugs/613560](https://bugs.launchpad.net/bugs/613560)

---

### Post by jpeddicord on 2010-08-05
Thanks for the heads-up. Bug [lpbug]612370[/lpbug] mentions that an upstream fix is available, so hopefully it won't be long for a fix.

I updated to 3.7.0-1 about an hour ago before I saw this. Started banshee just now and am not noticing anything extremely slow. I wonder what conditions actually cause it...

---

### Post by MacUntu on 2010-08-05
SQLite had performance? :P Maybe that's why sorting in Banshee failed with a couple of hundred songs.

Edit: Yupp, no problems with 3.6.22-1.

---

