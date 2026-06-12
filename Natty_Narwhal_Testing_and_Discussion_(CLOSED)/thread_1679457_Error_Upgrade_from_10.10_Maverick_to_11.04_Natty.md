---
title: "Error: Upgrade from 10.10 Maverick to 11.04 Natty"
date: 2011-02-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by suryateja.sun on 2011-02-01
Hai,

I browsed on internet to find how to upgrade to 11.04 and find the answer.

Press Alt+F2 and enter the command update-manager -d

After authentication, the manager showed the updates and at some point of time, I got the following error.

----
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_universe_ binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
----

Everytime I open Update Manager/Synaptic Package Manager, the following error encounters. Please help me in this regard.

I doubted its problem of sources.list file. I uploaded a copy of the file.

---

### Post by dino99 on 2011-02-01
gksu gedit /etc/apt/sources.list

change "maverick" by "natty", then save

sudo rm /var/cache/apt/archives/*

then update, upgrade (but be aware of xserver 1.9.99 issue, see related thread)

---

### Post by suryateja.sun on 2011-02-01
Thanks so much dino99. Will check xserver after the upgrade.

---

### Post by dino99 on 2011-02-01
> **suryateja.sun said:**
> Thanks so much dino99. Will check xserver after the upgrade.

not after, before (dont install the xserver packages, till they are completly updated)

---

