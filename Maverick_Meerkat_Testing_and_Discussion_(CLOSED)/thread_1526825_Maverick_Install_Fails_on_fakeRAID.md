---
title: "Maverick Install Fails on fakeRAID"
date: 2010-07-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ronparent on 2010-07-08
Similar to Lucid any attempt to install to an active fakeraid will fail unless no formatting or partitioning is needed to complete the install.:confused: This originates from the inability of gparted to see raid drives or partitions in a Lucid, Mint9, or Maverick boot environment. This behavior is not observable in gparted used in 9.04 and prior.

A workaround is to preformat any target partitions and to install without without any formatting. Gparted on the completed install will remain useless on the raid. 

Unlike 10.04 or Mint9, grub will now install to the designated raid array. I have reported this behavior as a bug: [https://bugs.launchpad.net/bugs/600729](https://bugs.launchpad.net/bugs/600729)
):P

---

### Post by NHclimber on 2010-08-19
Although lucid and maverick *installs* continue to be broken, upstream gparted has been fixed to work with firmware raid on lucid and maverick.  It is now possible to run gparted on lucid, pre-partition and format a raid volume (or partial) and install maverick to that.

---

### Post by ronparent on 2010-08-22
Actually, this is quite confusing. I just installed the alpha 3 (I know, I'm slow) with mixed results. When I tried to install and use kpartx in alpha 2, The whole system was frozen up by a process that couldn't be terminated (except with a hard reset). When I installed kpartx to the live cd there was no problem and I was able to install alpha 3 from there. When the installed alpha 3 was booted, the system had no installed gparted. I used sysnaptics to install 1st gparted, which didn't see the raid, 2nd kpartx which on calling gparted locked up my system again. In some ways this behavior is a regression, but, at least I don't have to pre-partition to install.

I don't know what explanations will be needed to the forum when the questions start coming. I'll be hoping that the eventual fix will be adequate.

---

### Post by ranch hand on 2010-08-22
We have had this same problem in 9.10 and 10.04 testing.  They were fine, mostly, when released.

In a 6 month release cycle, the final release is a long way away from now.

---

### Post by ronparent on 2010-09-04
All install problems to a fakeraid now appear fixed with the beta release.

---

