---
title: "can't install my webcam module"
date: 2006-09-30
forum: Multimedia &amp; Video
---

### Post by patcito on 2006-09-30
Hey all,
I did:
apt-get install module-assistant build-essential pwc-source

Then when I entered the pwc-source to install and type make, I get:
make[1]: Entering directory `/lib/modules/2.6.17-10-generic/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.17-10-generic/build'
make: *** [all] Error 2


How could I fix this?

thanx in advance

Pat

---

### Post by cobray on 2006-10-01
Did you do ./configure before you did make?
I assume it has a configure script

---

