---
title: "Right-click/copy crashes Firefox and Chromium"
date: 2010-12-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2010-12-23
After today's updates whenever I try to copy something from one Firefox tab or Chromium tab (by right-clicking > copy) it crashes both browsers.:o

I see there are 3 open jdk updates being held back due to a dependency thing. Would that be the cause?

---

### Post by cariboo on 2010-12-23
I've got the same problem, java shouldn't have anything to do with the problem.

---

### Post by Quackers on 2010-12-23
I've just run a few more updates and the dependency problem for open jdk has been fixed so they ran too.
All seems back to normal now.
Is yours fixed to cariboo907?

---

### Post by cariboo on 2010-12-23
The latest updates, seemed to have solved the problem for me too.

---

### Post by Harry33 on 2010-12-24
> **cariboo907 said:**
> The latest updates, seemed to have solved the problem for me too.

Yes this was an additional bug #693758, that appeared after a newer GTK+2.0_2.23.3-1ubuntu3. Now,  the newest version (a roll back version) 2.23.3.is.2.23.2-0ubuntu1 fixes this problem for now.

---

