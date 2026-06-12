---
title: "indicator-applet-appmenu memory leak: 786 MB"
date: 2011-02-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Starks on 2011-02-21
Mind you, this is over the course of a 3 day uptime, but still.

---

### Post by mc4man on 2011-02-22
Are you using the classic login? 
there is a memory leak in unity w/ the unity-panel-service that is a per use leak, 1MB+ per use of the global menu
In the classic it looks like it goes up a bit more per use

(there are also leaks in compiz w/ the dash and places.

---

### Post by Starks on 2011-02-22
Yeah, I'm in classic mode.

Got a bug #?

---

### Post by mc4man on 2011-02-22
Placed this on unity-panel service, though did mention the same occurs in Classic w/ indicator-applet-appmenu. (I figure they're related if not actually the same..?
It may be worth someone posting a comment concerning the applet to see.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/722972](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/722972)

(the leaks in dash, ect. are now showing fixed released which is good to see even though overall the effect, atm,  was nil, -  compiz will crash well before the loss is noticed

---

