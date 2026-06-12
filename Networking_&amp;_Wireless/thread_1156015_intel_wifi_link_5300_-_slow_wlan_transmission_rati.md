---
title: "intel wifi link 5300 - slow wlan transmission ratio"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by odesu on 2009-05-11
Hi,

my wlan transmission ratio isnt better than 50kbit/s in several networks. On Windows it works fine.
Im using the 2.6.28-12-generic kernel and the iwlagn module is loaded. Signal quality is ok and nobody broadcasts at my channel frequency.

What could i check next?

best regards, odesu

---

### Post by Peter09 on 2009-05-11
Have you checked your wireless drivers for bugs/upgrades

---

### Post by Peter09 on 2009-05-11
There is a hit of a new driver in the backport packages for Jaunty

---

### Post by odesu on 2009-05-11
> **Peter09 said:**
> Have you checked your wireless drivers for bugs/upgrades

Yes, everything is up to date. I found no bugs which reduce the bandwidth. Since kernel-2.6.26 the intel 5300 chip should be full supported.

best regards, odesu

---

### Post by Peter09 on 2009-05-11
So you have installed 

linux-backports-modules-jaunty-generic

---

### Post by odesu on 2009-05-11
> **Peter09 said:**
> So you have installed 

linux-backports-modules-jaunty-generic

Big THANKS to you!
Installing linux-backports-modules-jaunty-generic fixed the problem.
I thought only activating the jaunty-backports at the update-manager should be enough for updating my system.

best regards, odesu

---

