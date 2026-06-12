---
title: "Can't get past Python Issue"
date: 2010-12-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ubunturules on 2010-12-20
It seems like I've tried everything but I keep getting the same issue when I try to update.

E: pycompile:240: Requested versions are not installed
dpkg: error processing python2.7-minimal (--configure):
 subprocess installed post-installation script returned error exit status 3
Errors were encountered while processing:
 python2.7-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Harry33 on 2010-12-21
So when was the last time you had fully updated/upgraded Natty?
What package you are trying to update?
How do you try to update it?
Are you using other than official repos?

---

### Post by Frank Mehnert on 2010-12-21
Same here. My last update was some days ago and I don't have any extra repositories, only natty, natty-updates and natty-security.

The problem is that python2.7 minimal is updated before python-minimal so debpython/version.py does not return 2.7 as valid version.

---

### Post by Frank Mehnert on 2010-12-21
The quick fix is to edit /usr/share/python/debpython/version.py manually and change line 26 to

SUPPORTED = [(2, 6), (2, 7)]

---

### Post by Harry33 on 2010-12-21
Are we talking about the latest python package here?
python2.7_2.7.1-1ubuntu4 from 2010-12-14

I haven't had any such issues.

---

### Post by 1hutchy on 2010-12-30
Thanks Frank.That seemed to be the easiest fix I could Find

---

### Post by 1hutchy on 2010-12-30
Thanks Frank, That was the easiest Fix I could find

---

