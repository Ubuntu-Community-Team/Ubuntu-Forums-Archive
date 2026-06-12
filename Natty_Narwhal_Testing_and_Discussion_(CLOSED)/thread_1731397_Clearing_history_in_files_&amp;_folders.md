---
title: "Clearing history in files &amp; folders?"
date: 2011-04-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ELD on 2011-04-17
Is there a way or a planned way to clear your history in the recent part of files and folders?

---

### Post by Hogashi on 2011-04-17
Delete activity.sqlite in ~/.local/share/zeitgeist/

---

### Post by dino99 on 2011-04-17
look at bleachbit and gconf-cleaner

---

### Post by Mr. Picklesworth on 2011-04-17
An application to solve this in a slightly less destructive way is in the works: [http://devcando.wordpress.com/2011/04/15/please-say-welcome-to-the-first-draft-of-zeitgeist-global-privacy/](http://devcando.wordpress.com/2011/04/15/please-say-welcome-to-the-first-draft-of-zeitgeist-global-privacy/)

---

### Post by pulpo69 on 2011-04-20
Clearing history in files & folders?
Delete activity.sqlite in ~/.local/share/zeitgeist/

i can't find this file or folder. even not in the hidden ones.

---

### Post by pulpo69 on 2011-04-20
bleachbit don't work for this purpose.

---

### Post by Larkspur on 2011-04-20
> **pulpo69 said:**
> Clearing history in files & folders?
Delete activity.sqlite in ~/.local/share/zeitgeist/

i can't find this file or folder. even not in the hidden ones.


That's where the database is for me.  Do you have anything in ~/.cache/zeitgeist/ ?  If there's a file called demon.log, open it up and there should be a line near the start like this:

```
INFO - zeitgeist.sql - Using database:
```After the colon will be the path to wherever it is storing its info.  Check if zeitgeist-datahub is running as well.  I think that's the program that does all the snooping.

---

