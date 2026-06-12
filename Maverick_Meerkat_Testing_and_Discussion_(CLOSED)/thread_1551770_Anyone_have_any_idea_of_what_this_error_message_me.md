---
title: "Anyone have any idea of what this error message means?"
date: 2010-08-12
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by mdurham on 2010-08-12
Cheers

---

### Post by ranch hand on 2010-08-12
Usually means you already have it installed.

---

### Post by zekopeko on 2010-08-12
That error needs some serious rewording and polish.

---

### Post by mdurham on 2010-08-13
> **zekopeko said:**
> That error needs some serious rewording and polish.
I'd certainly agree with that. The question is: did it install correctly or not? (rhetorical question) 
Cheers, Mike

---

### Post by Peter09 on 2010-08-13
If you have a previous version of VirtualBox installed it is sometimes necessary to remove that before upgrading, could that be the problem?

---

### Post by taavikko on 2010-08-13
gdebi also gives a funny output when installing local .deb

---

### Post by cariboo on 2010-08-13
+1, I had problems with gdebi crashing yesterday. I had to use dpkg to install a package.

---

### Post by psyke83 on 2010-08-13
It seems to me that the package "virtualbox-3.2" is supposed set a Replaces or Conflicts flag against the package "virtualbox". Although you may think that the GUI is merely sloppy, it could in fact be a packaging bug.

---

### Post by sinurge on 2010-08-15
I agree it seems a Packaging bug. Would also advice though removing hte older package and then installing this one.

---

### Post by mdurham on 2010-08-15
> **sinurge said:**
> I agree it seems a Packaging bug. Would also advice though removing hte older package and then installing this one.
Thanks

---

