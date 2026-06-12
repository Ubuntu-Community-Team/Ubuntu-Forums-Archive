---
title: "MCE remote fails after updating"
date: 2008-05-08
forum: Mythbuntu
---

### Post by lerrup on 2008-05-08
I have just updated to Hardy and now my MCE-USB2 remote has stopped working.  

It does not appear in /dev ,irw does not work and I get the following output. 

dmesg | grep -i lirc 
[   32.737971] lirc_dev: disagrees about version of symbol struct_module
[   32.749947] lirc_mceusb2: disagrees about version of symbol struct_module
[  110.645757] lirc_dev: disagrees about version of symbol struct_module
[  110.662210] lirc_dev: disagrees about version of symbol struct_module
[  110.664102] lirc_mceusb2: disagrees about version of symbol struct_module
[ 2106.012642] lirc_dev: disagrees about version of symbol struct_module
[ 2106.014631] lirc_mceusb2: disagrees about version of symbol struct_module
[ 1174.894448] lirc_dev: disagrees about version of symbol struct_module
[ 1174.900933] lirc_dev: disagrees about version of symbol struct_module
[ 1174.902197] lirc_mceusb2: disagrees about version of symbol struct_module
[ 2872.018681] lirc_dev: disagrees about version of symbol struct_module
[ 2872.031016] lirc_dev: disagrees about version of symbol struct_module
[ 2872.033841] lirc_mceusb2: disagrees about version of symbol struct_module

I have tried reinstalling lirc, but the result is the same.  

Any ideas?

---

### Post by superm1 on 2008-05-08
> **lerrup said:**
> I have just updated to Hardy and now my MCE-USB2 remote has stopped working.  

It does not appear in /dev ,irw does not work and I get the following output. 

dmesg | grep -i lirc 
[   32.737971] lirc_dev: disagrees about version of symbol struct_module
[   32.749947] lirc_mceusb2: disagrees about version of symbol struct_module
[  110.645757] lirc_dev: disagrees about version of symbol struct_module
[  110.662210] lirc_dev: disagrees about version of symbol struct_module
[  110.664102] lirc_mceusb2: disagrees about version of symbol struct_module
[ 2106.012642] lirc_dev: disagrees about version of symbol struct_module
[ 2106.014631] lirc_mceusb2: disagrees about version of symbol struct_module
[ 1174.894448] lirc_dev: disagrees about version of symbol struct_module
[ 1174.900933] lirc_dev: disagrees about version of symbol struct_module
[ 1174.902197] lirc_mceusb2: disagrees about version of symbol struct_module
[ 2872.018681] lirc_dev: disagrees about version of symbol struct_module
[ 2872.031016] lirc_dev: disagrees about version of symbol struct_module
[ 2872.033841] lirc_mceusb2: disagrees about version of symbol struct_module

I have tried reinstalling lirc, but the result is the same.  

Any ideas?
remove the lirc-modules-source package.  It's unnecessary and causing conflicts.

---

