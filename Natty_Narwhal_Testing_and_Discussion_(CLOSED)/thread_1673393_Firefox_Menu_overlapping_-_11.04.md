---
title: "Firefox Menu overlapping - 11.04"
date: 2011-01-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by smuthavarapu on 2011-01-22
Is this happening in only my machine or any one can reproduce this.

Check screen attached, The menu is overlapping, this is not happening in Windows and I did not check in other Ubuntu versions.

This is Firefox Beta 8 [Edit] -- Its FireFox Beta 9
Natty 11.04

---

### Post by dino99 on 2011-01-22
in a terminal:

compiz --replace &

---

### Post by efflandt on 2011-01-22
Actually your screen shot shows 4.0 b9 (not b8 ).  You must be using **firefox-globalmenu** shown in [this thread]("http://ubuntuforums.org/showthread.php?t=1666311") because that does not seem to happen in my 4.0 b9 without that.  Report bugs for firefox-globalmenu [here]("https://bugs.launchpad.net/globalmenu-extension/+filebug")

---

### Post by smuthavarapu on 2011-01-22
> **efflandt said:**
> Actually your screen shot shows 4.0 b9 (not b8 ).  You must be using **firefox-globalmenu** shown in [this thread]("http://ubuntuforums.org/showthread.php?t=1666311") because that does not seem to happen in my 4.0 b9 without that.  Report bugs for firefox-globalmenu [here]("https://bugs.launchpad.net/globalmenu-extension/+filebug")

Yeah, thank you, will follow your link to create the Bug

---

### Post by chrisccoulson on 2011-01-22
I'm not entirely sure how that extension can cause menu popups to appear underneath other menus, it has no control or influence on that at all.

In any case, the real bug is that the menu button is displayed at all, but that's something I'm already working on.

---

