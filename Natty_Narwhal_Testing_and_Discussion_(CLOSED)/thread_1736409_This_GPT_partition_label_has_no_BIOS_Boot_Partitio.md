---
title: "This GPT partition label has no BIOS Boot Partition"
date: 2011-04-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Yahoé on 2011-04-22
Bonjour,

On Ubutu Natty fully during update of grub-PC I got this error message.

Could someone explain what this is about:

Paramétrage de grub-pc (1.99~rc1-13ubuntu3) ...
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
Installation finished. No error reported.
Generating grub.cfg ...

Regards.

---

### Post by VMC on 2011-04-22
Download boot_info_script (see my link), then copy&paste RESULTS.txt file.

Also read this [_**topic**_]("http://ubuntuforums.org/showthread.php?t=1719851&page=6"), starting around post#51, might help.

---

### Post by oldfred on 2011-04-22
Some more info on bios_grub gpt partition, since it is gpt it can be anywhere on drive:

grub2 & GPT info
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)
In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged.

If you have gpt you need another small (8-32mb) partition for grub. Are you using efi or BIOS compatible mode?
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
"unknown" filesystem! may be shown
However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. Make it 128 kiB as recommended in the following link. Actually, using ext2 for example, and GParted Live CD, the minimum partition size is 8 MB, or 32 MB for FAT32. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
sudo parted /dev/sda set <partition_number> bios_grub on

It only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues

This link says they just installed grub2 to the drive and it found the BIOS boot partition.
[http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html](http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html)
Legacy BIOS issues with gpt
[http://www.rodsbooks.com/gdisk/bios.html](http://www.rodsbooks.com/gdisk/bios.html)

---

### Post by srs5694 on 2011-04-22
Oldfred's information is good; however, it appears he's copied recommendations from at least three sources, each of which has different recommendations for the size of the BIOS Boot Partition (8-32MB, 128KiB, and 32KiB-1MiB), which may lead to confusion. The minimum space requirement for this partition is about 32KiB, but it's wise to make it bigger than that in case future versions of GRUB require a bigger space. Partitioning tools sometimes impose their own requirements or make a larger size sensible. If you've already got partitions with data on your disk, they may impose their own unique limits. Seeing the output of the following command can help us determine what will fit:

```

sudo parted /dev/sda unit s print

```

Please post the results here between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings to retain legibility. The Boot Info Script that VMC suggested will provide similar information, but is not otherwise required.

---

