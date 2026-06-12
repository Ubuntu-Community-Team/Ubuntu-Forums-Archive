---
title: "installing graphics drivers not as sudo?"
date: 2012-09-11
forum: Multimedia Software
---

### Post by abraxas334 on 2012-09-11
Hi I was wondering it is at all possible to install a grphics driver not as root, i.e using sudo?

Thanks!

---

### Post by ratcheer on 2012-09-11
I have never seen anything indicating that that could be done.

Tim

---

### Post by Bucky Ball on 2012-09-11
When you use sudo you are basically becoming root for that command only, ie:

```
sudo apt-get update
```

You can not, therefore, install graphics drivers, and many other things, without either becoming root or sudo-ing the command. 

sudo = superuser do! In other words, you have root privileges for that command. Not sure what graphics you are attempting to install but:

```
make
sudo make install
```

... would probably work, if those commands are required, without need to issue:

```
sudo su
```

... before everything to become root first. Just curious: Why are you bothered/want to know? For what purpose don't you want to become root?


*Thread moved to **Multimedia & Video** ...*

---

