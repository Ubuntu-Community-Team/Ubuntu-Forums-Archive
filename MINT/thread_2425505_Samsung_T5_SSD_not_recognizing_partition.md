---
title: "Samsung T5 SSD not recognizing partition"
date: 2019-08-26
forum: MINT
---

### Post by HerzyWSU on 2019-08-26
Hi everyone.

I inherited a Samsung T5 SSD (1TB) that was encrypted when I received it.  I would like to reformat the entire drive to NTFS or ext4.

I ran gparted on the drive, and that is only recognized a 42 MB partition used used to hold the Samsung encryption software on SSD.  Presumably, there is another partition on the system that gparted isn't able to recognize.

How can I recover the unrecognized partition.

FWIW I'm running Linux Mint 19.2 Cinnamon.

---

### Post by oldfred on 2019-08-26
Moved to Mint sub-forum.

sudo hdparm -I /dev/sdX #where X is your drive like sda, or sdb.

       Erase SSD
[https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)
[https://wiki.archlinux.org/index.php/Solid_State_Drives/Memory_cell_clearing](https://wiki.archlinux.org/index.php/Solid_State_Drives/Memory_cell_clearing)
[https://www.thomas-krenn.com/en/wiki/SSD_Secure_Erase](https://www.thomas-krenn.com/en/wiki/SSD_Secure_Erase)
[https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)

---

