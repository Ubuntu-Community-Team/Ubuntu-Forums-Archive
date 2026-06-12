---
title: "Installed MythTV from apt, is myth.rebuilddatabase.pl included anywhere?"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by Yoooder on 2007-03-03
I've been using MythTV for a while, and would like to use it as an all-in-one media center.  I have a large collection of videos that I would like to import, but the only way that I have heard of is using the myth.rebuilddatabase.pl script, which I haven't found anywhere on my machine.

Is there another means of importing video, is this script installed with a different deb package, or will I need to reinstall from a different source?

---

### Post by superm1 on 2007-03-04
wget  "http://svn.mythtv.org/trac/browser/trunk/mythtv/contrib/myth.rebuilddatabase.pl?format=raw" -O myth.rebuilddatabase.pl

---

### Post by Yoooder on 2007-03-05
Thanks :)

---

### Post by superm1 on 2007-03-05
In the future (feisty+), for people who come across this thread:

mythtv-backend will install the entire contrib directory to /usr/share/doc/mythtv-backend.

---

