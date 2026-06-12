---
title: "Upgrading 9.04 -&gt; 9.10: temporary space solution"
date: 2009-11-25
forum: Mythbuntu
---

### Post by port443 on 2009-11-25
Hi, I'm running 9.04 front-end only on a 4Gb stick.  It has ~0.5Gb free.
Now when I try to upgrade to 9.10 it tells me I need ~0.5Gb more on **/**.
I may attach another 2Gb USB drive temporary to do upgrade, but how can I point upgrade scripts to some other location aside from **/** ?

(I assume 9.10 did not grow 1Gb larger than 9.04, am I right? :))

---

### Post by samarium on 2009-12-08
> **port443 said:**
> Hi, I'm running 9.04 front-end only on a 4Gb stick.  It has ~0.5Gb free.
Now when I try to upgrade to 9.10 it tells me I need ~0.5Gb more on **/**.
I may attach another 2Gb USB drive temporary to do upgrade, but how can I point upgrade scripts to some other location aside from **/** ?

(I assume 9.10 did not grow 1Gb larger than 9.04, am I right? :))

Assuming the 2G mounts at /media/2GUSB, and you have already formatted it as ext3 or ext4, then try

apt-get autoremove # flush old packages
mount --bind /media/2GUSB /var/cache/apt/archives

and then try the upgrade, and the 2G stick will be used for temporary .deb package storage while doing the upgrade.  After you reboot, /var/cache/apt/archives will be as before, and you may have some .deb files on your 2GUSB that you want to manually clean.

---

