---
title: "How can I read a mdf file on ubuntu 7.10"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by yinglcs2 on 2007-11-02
Hi, 

How can I read a mdf file on ubuntu 7.10?
Any program I need to install?

Thank you.

---

### Post by shad0w_walker on 2007-11-02
I'm not sure how to mount the mdf file (Not got any about) but there is a tool i used a while back (To get rid of the mdf files acctually) called mdf2iso. It should be the repos so install it and run it from a terminal like so:

mdf2iso <mdf filename> <destination filename>

You should be able to view the contents of .iso files using the archive manager.

---

### Post by ruibernardo on 2007-11-02
Install the package mdf2iso and run

```
mdf2iso filename.mdf filename.iso
```Now you can read it.8-)

---

