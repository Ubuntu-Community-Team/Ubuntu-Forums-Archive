---
title: "Cannot upgrade"
date: 2011-04-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by tajreed on 2011-04-05
I receive the following messages-

E:Encountered a section with no Package: header,
E:Problem with MergeList /var/lib/apt/lists/

us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Any thoughts?

---

### Post by cariboo on 2011-04-05
Have you tried deleting /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_bina ry-i386_Packages, then updating again?

---

### Post by tajreed on 2011-04-05
Hey, you're a genius Cariboo, I deleted everything under "List" and everything is OK.

Thanks

---

