---
title: "kdenlive not starting on Oneiric"
date: 2011-10-25
forum: Multimedia Software
---

### Post by shantiq on 2011-10-25
Cryptic [to me] message   attached


Anyone knows how to fix that?

---

### Post by dniMretsaM on 2011-10-25
Lol I just ran into this today, too. Run this in terminal to fix the problem:
```
sudo add-apt-repository ppa:sunab/kdenlive-svn
sudo apt-get update
sudo apt-get dist-upgrade
```Apparently the version in the default repos expects the package [FONT=Courier New]mlt[/FONT] to be installed, but it isn't a dependency to the Kdenlive package. And as far as I can tell, it isn't even in the default repos.

---

### Post by shantiq on 2011-10-25
thanx man brilliant

i shall not even pretend that i understand what was missing and why


just happy to have it back    love that program    :KS

---

