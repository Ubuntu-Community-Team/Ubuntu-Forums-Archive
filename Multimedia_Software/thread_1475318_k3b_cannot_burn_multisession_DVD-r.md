---
title: "k3b cannot burn multisession DVD-r"
date: 2010-05-06
forum: Multimedia Software
---

### Post by wandalalakers on 2010-05-06
Can someone please explain what this means in plain english?
I get the same error as this person below.
It appears that this bug has already been reported.
I'm trying to continue burning two multsessions CDs that were created with an earlier version of k3b (kubuntu 8.04)

[http://imagebin.ca/view/eIywHR.html](http://imagebin.ca/view/eIywHR.html)

[http://bugs.kde.org/show_bug.cgi?id=230742](http://bugs.kde.org/show_bug.cgi?id=230742)

   Description From  Piotr Mitas   2010-03-14 19:09:19   (-) [reply]

Version:           1.90.0 (using 4.4.1 (KDE 4.4.1), Gentoo)
Compiler:          x86_64-pc-linux-gnu-gcc
OS:                Linux (x86_64) release 2.6.33-gentoo

I have an appendable DVD-R with a 1.4 GB file on it. I want to write a 2GB file
to this disc. K3B displays the writing window and then this:
[http://imagebin.ca/view/eIywHR.html](http://imagebin.ca/view/eIywHR.html). If I try writing a smaller file, it works
fine.

------- Comment #1 From Micha&#322; Ma&#322;ek 2010-03-14 23:13:14 (-) [reply] -------

SVN commit 1103356 by mmalek:

Wait for medium with the remaining size of last session not the whole disk.
BUG: 230742

---

