---
title: "Installation fails due to inactive raid"
date: 2009-11-11
forum: Mythbuntu
---

### Post by dlouwers on 2009-11-11
Hi,

I was trying to install MythBuntu 9.10 on a system that has nvraid disabled but previously had mirrored disks running XP. Apparently disabling RAID in BIOS didn't prevent Ubumtu from detecting RAID since I had but one disk to choose from named nvraidxxxxx. Installation on this device went OK but it failed to install GRUB on it in the end so it cannot boot.

Does anyone know how to prevent the installer from mistakenly seeing the raid array?

Best,

Dirk Louwers

---

### Post by yonkiman on 2009-11-11
I had [the same problem]("http://ubuntuforums.org/showthread.php?t=1307643").  I just ended up physically disconnecting all the RAID drives while I did the initial install.  Everything worked fine after that.

I suppose I should have filed a bug report for it but I'm not sure how or where to do that...

---

### Post by dlouwers on 2009-11-11
I did the same. I enabled RAID in the BIOS and removed all disks from the array and disabled RAID again in the BIOS. So it seems that dmraid ignores the flag in the BIOS and just goes ahead and reads the RAID settings.

On the other hand, I should be able to install using SATA-raid without this GRUB error as well. Did you manage to find out how to manualy install grub after the installation procedure failed?

Best,

Dirk Louwers

---

