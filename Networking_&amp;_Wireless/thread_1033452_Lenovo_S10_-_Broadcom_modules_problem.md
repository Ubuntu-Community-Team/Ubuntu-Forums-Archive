---
title: "Lenovo S10 - Broadcom modules problem"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by decker on 2009-01-07
Ok, so i've got 8.10 on my lappy. It rocks, most things work. Except for wireless. I download the latest drivers for this chipset and i can compile them and install them. Everything works great.

My problem is with the modules. It uses wl.ko which resides in /lib/modules/2.6.27-9-generic/volatile/
I rmmod the wl.ko. Delete the wl.ko in the volatile directory. replace it with the new wl.ko. Run "modprobe wl" and then "/etc/init.d/networking restart". And everything works perfectly. 

BUT, when i reboot, the module in the volatile directory reverts back to the old module which doesn't work. So i had to write a script that constantly checks the md5sum of the module and replaces it with the good one. 

my question is, is there someway to make this permanent without having to script-fix it? Where do the volatile modules come from and is there a way to change it at it's source?

Any help would be hugely appreciated! Thanks!

---

### Post by Ayuthia on 2009-01-07
Not for sure if this will help or not, but have you tried using sudo depmod -a after you copied the file?  You might try creating another directory for the wl.ko file, remove the one in volatile, and make sure that the Broadcom STA module is not loaded in Hardware Drivers.  The wl.ko module comes from the linux-restricted-modules package if I recall correctly.

---

### Post by decker on 2009-01-07
> **Ayuthia said:**
> Not for sure if this will help or not, but have you tried using sudo depmod -a after you copied the file?  You might try creating another directory for the wl.ko file, remove the one in volatile, and make sure that the Broadcom STA module is not loaded in Hardware Drivers.  The wl.ko module comes from the linux-restricted-modules package if I recall correctly.

The STA module is definitely not loaded in the hardware drivers.I tried runing depmod after swapping the wl.ko driver. Still no luck.

I can delete the wl.ko original driver and after a reboot it comes back. Not sure from where.

---

