---
title: "[SOLVED] Upgrade to .21 from .20.2?"
date: 2008-03-13
forum: Mythbuntu
---

### Post by saxuntu on 2008-03-13
I upgraded my mythbuntu backend to .21 using the update manager. I did this thinking it would be just as easy on my Ubuntu front ends, no such luck. I checked the repos and .21 isn't there for my ubuntus, but is there with mythbuntu. I checked and their both supposedly in the multiverse. Ideas?

---

### Post by Phydeaux on 2008-03-13
Here is my sources.list, I think the upgrade was in backports.

```
deb http://debian.slimdevices.com unstable main
deb http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy universe multiverse main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

deb http://packages.medibuntu.org/ gutsy free non-free

```

---

### Post by nasha on 2008-03-14
Confirming that 0.21 is in the backports repo :)

---

### Post by saxuntu on 2008-03-16
done and done. Thanks guys.

---

