---
title: "If you are using or testing ubuntuone"
date: 2010-08-22
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by mc4man on 2010-08-22
Then you should keep in mind there are a couple of open bugs, the more significant is [this one]("https://bugs.launchpad.net/ubuntu-sso-client/+bug/617041") (100% use of 1 cpu
Note that it won't occur until you open ubuntuone preferences, after which only a log out or killing the process will stop

---

### Post by kyleabaker on 2010-08-22
I haven't noticed this before, but does the underlying cause happen to be related to subprocess calls? I noticed that GM-Notify does the same thing when you click on your inbox from the indicator menu and I traced it back to subprocess.call().

If so, it may not be due to UbuntuOne, but another library. Not sure though.

---

### Post by mc4man on 2010-08-25
Resolved with the updates of ubuntuone-* tonight.
The music store (rhythmbox import bug) was also fixed

(as was one of two serious gdebi-gtk bugs

---

