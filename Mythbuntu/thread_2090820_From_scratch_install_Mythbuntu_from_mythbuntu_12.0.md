---
title: "From scratch install Mythbuntu from mythbuntu 12.04 CD cannot install grub"
date: 2012-12-03
forum: Mythbuntu
---

### Post by keepitsimpleengr on 2012-12-03
My 2yr old Mythtv system suffered catastrophic failure, so here I am starting over.

I downloaded the Mythbuntu 12.04 cd, checked M5, burned and installed.  Simple 40GB root and 8GB swap.  At the end of install, the installation reports: fatal error, unable to install grub. :(

If I chroot to the install directory, run update-grub and grub-install, when I reboot the system hangs with the splash screen, I'm not sure if it's one or two problems, but I sure miss Mythtv....

---

### Post by keepitsimpleengr on 2012-12-03
Fifth attempt succeeded.

Only thing I did different was to not leave unallocated space on install drive.

---

