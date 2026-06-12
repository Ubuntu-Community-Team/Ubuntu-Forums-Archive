---
title: "Amarok 2 in ubuntu 8.10"
date: 2008-12-14
forum: Multimedia Software
---

### Post by murthy on 2008-12-14
I read in the web that amarok 2 has been released and find that version in the synaptic package manager which shows that it is installed.  However when I play amarok it shows the version as 1.4.10 (using KDE 3.5).  I have kubuntu and Xubuntu also installed.  Kindly let me know how I can use latest version of amarok?

---

### Post by SuperSonic4 on 2008-12-14
Have you opened backports?

What if you add

```
deb http://ppa.launchpad.net/kubuntu-experimental/ubuntu intrepid main
``` to /etc/apt/sources.list and update

---

