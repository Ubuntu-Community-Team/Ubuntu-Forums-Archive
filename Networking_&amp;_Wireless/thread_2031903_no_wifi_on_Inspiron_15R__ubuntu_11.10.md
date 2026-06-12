---
title: "no wifi on Inspiron 15R  ubuntu 11.10"
date: 2012-07-22
forum: Networking &amp; Wireless
---

### Post by ub2011 on 2012-07-22
Just installed ubuntu 11.10 on Inspiron 15R.  Wired ethernet works, but wireless does NOT work.  dmesg tells me that iwlagn request for  firmware file "iwlwifi-2030-5.ucode' failed.   Sure enough, there is no such file in /lib/firmware.

there is a 2030-6, but the kernel won't take it (i tried copying it into a -5.ucode)

i've looked on web for -5 version, but all i find is -6.

kernel is 3.0.0-23-generic-pae

help

---

### Post by ub2011 on 2012-08-06
> **ub2011 said:**
> Just installed ubuntu 11.10 on Inspiron 15R.  Wired ethernet works, but wireless does NOT work.  dmesg tells me that iwlagn request for  firmware file "iwlwifi-2030-5.ucode' failed.   Sure enough, there is no such file in /lib/firmware.

there is a 2030-6, but the kernel won't take it (i tried copying it into a -5.ucode)

i've looked on web for -5 version, but all i find is -6.

kernel is 3.0.0-23-generic-pae

help

installing 12.04 solved problem

---

