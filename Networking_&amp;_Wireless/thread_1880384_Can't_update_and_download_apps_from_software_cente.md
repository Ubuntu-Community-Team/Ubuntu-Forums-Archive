---
title: "Can't update and download apps from software center"
date: 2011-11-13
forum: Networking &amp; Wireless
---

### Post by Pjautuvas on 2011-11-13
Hello, after I tried to install Gimp single window mode, there was a power outage. After some minutes, when I can turn on PC, there was an error: Package system is damaged" I fixed that with update, but now when I want to update system it says: To perform this operation, install the packages from source, whose identity has not been established. When I try to install application for software center or synaptic it says check your internet connection. How to fix it?

P.S. Sorry for my poor English

---

### Post by praseodym on 2011-11-13
Hi,

try the following:

```
sudo dpkg --configure -a
sudo apt-get -f install
```
Even if it doesnt work, show the outputs of the terminal here.

---

### Post by Pjautuvas on 2011-11-14
Thanks, it helped for me :)

EDIT: Same problem again after restarting PC :(

Read package lists ... completed
Dependency tree constructed
Reading state information ... completed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

---

### Post by Pjautuvas on 2011-11-15
bump           .

---

### Post by praseodym on 2011-11-15
Try now:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
```

---

