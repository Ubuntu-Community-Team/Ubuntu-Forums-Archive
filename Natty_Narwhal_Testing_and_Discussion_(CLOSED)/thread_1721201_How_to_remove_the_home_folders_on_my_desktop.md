---
title: "How to remove the home folders on my desktop"
date: 2011-04-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by scottmuz on 2011-04-04
I upgraded to 11.04 from 10.04.

However I've got all the folders in my home directory as Icons on my desktop
(see attached screenshot).

Looking at unity screenshot of other users this doesn't seem normal.

How do I remove them?

---

### Post by scottmuz on 2011-04-04
Fixed. Not sure why but I needed to edit ~/.config/user-dirs.dirs so that XDG_DESKTOP_DIR wasn't $HOME.

---

