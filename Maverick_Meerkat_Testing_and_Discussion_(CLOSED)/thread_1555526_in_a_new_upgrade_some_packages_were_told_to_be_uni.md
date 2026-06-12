---
title: "in a new upgrade some packages were told to be uninstalled"
date: 2010-08-18
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by felixonmars on 2010-08-18
These packages were told to uninstall,
kdelibs5{u} libkde3support4{u} libkimproxy4{u} 

should the action be performed?

---

### Post by philinux on 2010-08-18
> **felixonmars said:**
> These packages were told to uninstall,
kdelibs5{u} libkde3support4{u} libkimproxy4{u} 

should the action be performed?

I use this. I never use update manager during testing.

```
sudo aptitude update && sudo aptitude safe-upgrade
```

Please see this sticky too. [http://ubuntuforums.org/showthread.php?t=1479146](http://ubuntuforums.org/showthread.php?t=1479146)

---

### Post by felixonmars on 2010-08-18
it is JUST cut from the output of aptitude safe-upgrade

---

### Post by philinux on 2010-08-18
> **felixonmars said:**
> it is JUST cut from the output of aptitude safe-upgrade

Did you read the link I gave you?

---

### Post by felixonmars on 2010-08-18
> **philinux said:**
> Did you read the link I gave you?

Sorry I did not read the long version, but now I follow the instruction to search in the maverick changes maillist by date, I cannot find a kdelibs-related upgrading...

---

### Post by MadCow108 on 2010-08-18
this may mean the repository is out of sync.
Just wait a while and it will probably disappear

---

### Post by mc4man on 2010-08-18
Upen up synaptic, search those packages and you can probably get a better idea.
Most likely aptitude considers them no longer needed  - for instance kdelibs5 is a transitional package

---

