---
title: "Darktable doesn't start upon installation"
date: 2011-10-19
forum: Multimedia Software
---

### Post by marer13 on 2011-10-19
Hi,

I have just installed Darktable and I'm trying to run it but it doesn't start. I even tried to start it from Terminal and that's what I get:

> marer13@marer13-Studio:~$ darktable

(darktable:12796): GConf-WARNING **: Got Disconnected from DBus.

Segmentation fault
marer13@marer13-Studio:~$

---

### Post by biggerben on 2011-11-25
I get the same error, using kubuntu 11.10 amd64

---

### Post by McNils on 2011-11-25
I have had problems with programs that wont start, like kdiff3.
The problem then has been solved by exporting some variables,

export $(dbus-launch)

But I dont know if it helps your problem. It could be some missing gnome stuff.

---

### Post by biggerben on 2011-11-25
upgrading to the newest darktable 0.9.3 via the unstable ppa solves this problem!

---

