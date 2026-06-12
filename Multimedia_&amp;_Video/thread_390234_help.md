---
title: "help"
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by dmm1983 on 2007-03-21
which repositry do people reccommend to use out of the seveas packages or any other one that anyone reccommends to use due to the fact plf does not exist

---

### Post by ajgreeny on 2007-03-21
Have a look at medibuntu repos which contain most if not all the packages previously in the plf repos.

## Medibuntu - Ubuntu 6.06 LTS "dapper drake"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free

Note these are for dapper 6.06, but I presume there are others for edgy etc.

---

### Post by dmm1983 on 2007-03-21
deleted

---

### Post by dmm1983 on 2007-03-21
delete

---

### Post by ajgreeny on 2007-03-22
In a terminal type:-
wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
This should get you the key needed.  Sorry, I forgot about that when I gave you the repos.

---

