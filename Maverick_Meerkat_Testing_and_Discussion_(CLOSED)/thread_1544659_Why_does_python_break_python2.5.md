---
title: "Why does python break python2.5?"
date: 2010-08-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by felixonmars on 2010-08-02
The following extra packages will be installed:
   python-dev (2.6.5-10ubuntu1)
   python-minimal (2.6.5-10ubuntu1)
Suggested packages:
   python-doc (2.6.5-10ubuntu1)
   python-profiler (2.6.5-0ubuntu1)
The following packages will be REMOVED:
   python2.5 (2.5.4-1ubuntu6)
   python2.5-minimal (2.5.4-1ubuntu6)
The following packages will be upgraded:
   python (2.6.5-0ubuntu1 => 2.6.5-10ubuntu1)
   python-dev (2.6.5-0ubuntu1 => 2.6.5-10ubuntu1)
   python-minimal (2.6.5-0ubuntu1 => 2.6.5-10ubuntu1)
3 upgraded, 0 newly installed, 2 to remove

---

### Post by seeker5528 on 2010-08-02
I don't know how long it's been since 2.5 was the default version or how long it has been since 2.5 was removed from the repositories, but they are not in the Maverick repositories, searching for python2.5 at [http://packages.ubuntu.com](http://packages.ubuntu.com) it looks like Karmic was the last version to include it.

Since python2.6 is the only supported version in Maverick, the unversioned python packages were adjusted accordingly and set to conflict with python2.5. I suspect it is less about what is known to be broken and more about what problems may result if people are allowed to keep their old, no-longer supported version of python during an upgrade.

Later, Seeker

---

