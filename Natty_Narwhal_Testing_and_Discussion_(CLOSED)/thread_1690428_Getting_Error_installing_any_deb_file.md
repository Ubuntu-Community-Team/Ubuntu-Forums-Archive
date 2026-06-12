---
title: "Getting Error installing any deb file"
date: 2011-02-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by smuthavarapu on 2011-02-18
I am getting the following Error if i try to install any deb file using Software Center.

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 885, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 997, in _simulate_helper
    trans.packages[PKGS_INSTALL] = [deb.pkgname]
TypeError: 'dbus.Struct' object does not support item assignment


Any Help ?

---

### Post by mc4man on 2011-02-18
For the moment either install and use gdebi or use dpkg for dl'ed .debs
dpkg -i /path/to/whatever.deb

The bug is in aptdaemon, shows fix committed but not yet released
[https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/702217](https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/702217)

---

### Post by smuthavarapu on 2011-02-18
Thank you that worked for me.

---

