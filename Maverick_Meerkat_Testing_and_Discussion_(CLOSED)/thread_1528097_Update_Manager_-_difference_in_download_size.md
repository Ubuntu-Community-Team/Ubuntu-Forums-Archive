---
title: "Update Manager - difference in download size"
date: 2010-07-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by chrismine on 2010-07-10
Cannot remember if I ever noticed before but when update manager shows the updates needs to be done it also gives the download size, but the applying changes shows a different size (screenshot attached) - can somebody shed light or is it a bug?

---

### Post by Longinus00 on 2010-07-10
This is probably the result of the devs implementing the new units policy[1] in a haphazard manner as the difference is the difference between MB and MiB[2].

[1] [https://wiki.ubuntu.com/UnitsPolicy](https://wiki.ubuntu.com/UnitsPolicy)
[2] [http://www.wolframalpha.com/input/?i=97.4+mebibyte+in+megabyte](http://www.wolframalpha.com/input/?i=97.4+mebibyte+in+megabyte)

---

### Post by chrismine on 2010-07-10
Longinus00 - thank you that explains it.

---

### Post by yelo3 on 2010-07-10
Anyway this needs a bug in launchpad

---

