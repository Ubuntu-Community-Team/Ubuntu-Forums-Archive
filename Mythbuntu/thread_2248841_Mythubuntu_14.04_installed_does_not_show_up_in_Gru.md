---
title: "Mythubuntu 14.04 installed does not show up in Grub"
date: 2014-10-17
forum: Mythbuntu
---

### Post by Callmestupid on 2014-10-17
I just installed Mythubuntu 14.04 along side Ubuntu 14.04. When I rebooted the Mythubuntu was not in the Grub menu to choose.Boots into regular Ubuntu istead.

---

### Post by ajgreeny on 2014-10-17
From Ubuntu run command **sudo update-grub** which may add back the Mythbuntu that is missing.
If you installed on the same hard drive as Ubuntu Mythbuntu should have taken over managing grub, but if you have more than one disk and put Mythbuntu on a separate one, using the Something Else option, where did you choose to install the bootloader?

---

### Post by Callmestupid on 2014-10-17
I tried the sudu update-grub there was only one partition that showed Ubuntu 14.04 LTS which was sdf7 all the other ertries were 13.04 and 13.10. All my drives except one show and MBR. There is one Ubuntu which just sqays Ubuntu which brings me into the regular Ubuntu. The 14.04 Ubuntu 14.04 LTS entry hangs up after the menu for Grub disappears. I have a self built computer. Contains:

Motherboard: Socket-AM2 Motherboard, MSI K9N SLI V2, NVIDIA® nForce 570LT SLI, DDR2 (MS-7390)

Media Card: Hauppauge WinTV-PVR 500 

OS: Ubuntu 14.04 LTS

OS 2: Mythubuntu: 14.04

Device Name: randell-MS-7390

Memory:  7.8 GB

Processor: AMD Phenom(tm) 9500 Quad-Core Processor × 4 

Graphics: Gallium 0.4 on AMD CEDAR

OS Type: 64-bit

Disk: 2.0 TB

---

### Post by ajgreeny on 2014-10-18
Just to check things a bit further can you show the output of ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
```which will show all the entries in the grub menu, including all those that are in the Advanced (ie, extra) section of the menu.

Also let's see output from ```
sudo fdisk -l
```It will not tell us which OS is in each partition but it may give some clues if you know the sizes of certain of your partitions.

---

### Post by Callmestupid on 2014-10-19
randell@randell-MS-7390:~$ grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnu
	menuentry 'Ubuntu, with Linux 3.13.0-37-generic' --class ubuntu --class gnu-linux --class gnu --cla
	menuentry 'Ubuntu, with Linux 3.13.0-37-generic (recovery mode)' --class ubuntu --class gnu-linux -
	menuentry 'Ubuntu, with Linux 3.13.0-36-generic' --class ubuntu --class gnu-linux --class gnu --cla
	menuentry 'Ubuntu, with Linux 3.13.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux -
	menuentry 'Ubuntu, with Linux 3.13.0-34-generic' --class ubuntu --class gnu-linux --class gnu --cla
	menuentry 'Ubuntu, with Linux 3.13.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux -
	menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --cla
	menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux -
	menuentry 'Ubuntu, with Linux 3.13.0-30-generic' --class ubuntu --class gnu-linux --class gnu --cla
	menuentry 'Ubuntu, with Linux 3.13.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux -
	menuentry 'Ubuntu, with Linux 3.13.0-29-generic' --class ubuntu --class gnu-linux --class gnu --cla
	menuentry 'Ubuntu, with Linux 3.13.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux -
	menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --cla
	menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux -
menuentry 'Memory test (memtest86+)' {
menuentry 'Memory test (memtest86+, serial console 115200)' {
menuentry "Ubuntu 13.04 (13.04) (on /dev/sdf5)" --class gnu-linux --class gnu --class os $menuentry_
menuentry "Ubuntu (on /dev/sdf5)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osp
menuentry "Ubuntu, with Linux 3.8.0-19-lowlatency (on /dev/sdf5)" --class gnu-linux --class gnu --cl
menuentry "Ubuntu, with Linux 3.8.0-19-lowlatency (recovery mode) (on /dev/sdf5)" --class gnu-linux 
menuentry "Ubuntu 14.04.1 LTS (14.04) (on /dev/sdf7)" --class gnu-linux --class gnu --class os $menu
menuentry "Ubuntu (on /dev/sdf7)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osp
menuentry "Ubuntu, with Linux 3.13.0-32-generic (on /dev/sdf7)" --class gnu-linux --class gnu --clas
menuentry "Ubuntu, with Linux 3.13.0-32-generic (recovery mode) (on /dev/sdf7)" --class gnu-linux --
randell@randell-MS-7390:~$ 


Thank you for looking at this.

---

### Post by Callmestupid on 2014-10-19
Sorry I thought I'd done both when I sent the other, but forgot to pastye the second one.


randell@randell-MS-7390:~$ sudo fdisk -l
[sudo] password for randell: 

Disk /dev/sda: 32.0 GB, 32015679488 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62530624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ea97d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    62529535    31263744    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x10efba30

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   488392064   244196001    c  W95 FAT32 (LBA)

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00041767

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048  1936748543   968373248   83  Linux
/dev/sdd2      1936750590  1953523711     8386561    5  Extended
/dev/sdd5      1936750592  1953523711     8386560   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.

Note: sector size is 4096 (not 512)

Disk /dev/sdc: 3000.6 GB, 3000592977920 bytes
255 heads, 63 sectors/track, 45600 cylinders, total 732566645 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1   732566644  2930266576   ee  GPT

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x079aab08

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1              63  1621012859   810506398+   7  HPFS/NTFS/exFAT
/dev/sdh2      1621014526  1953523711   166254593    5  Extended
/dev/sdh5   *  1820704768  1936750591    58022912   83  Linux
/dev/sdh6      1936752640  1953523711     8385536   82  Linux swap / Solaris
/dev/sdh7      1621014528  1820704767    99845120   83  Linux

Partition table entries are not in disk order

Disk /dev/sdg: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1              32    31266815    15633392    c  W95 FAT32 (LBA)

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x538cab66

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048  1936748543   968373248   83  Linux
/dev/sde2      1936748544  1953523711     8387584   82  Linux swap / Solaris
randell@randell-MS-7390:~$

---

### Post by Callmestupid on 2014-10-19
Sorry I thought I'd done both when I sent the other, but forgot to pastye the second one.


randell@randell-MS-7390:~$ sudo fdisk -l
[sudo] password for randell: 

Disk /dev/sda: 32.0 GB, 32015679488 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62530624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ea97d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    62529535    31263744    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x10efba30

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   488392064   244196001    c  W95 FAT32 (LBA)

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00041767

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048  1936748543   968373248   83  Linux
/dev/sdd2      1936750590  1953523711     8386561    5  Extended
/dev/sdd5      1936750592  1953523711     8386560   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.

Note: sector size is 4096 (not 512)

Disk /dev/sdc: 3000.6 GB, 3000592977920 bytes
255 heads, 63 sectors/track, 45600 cylinders, total 732566645 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1   732566644  2930266576   ee  GPT

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x079aab08

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1              63  1621012859   810506398+   7  HPFS/NTFS/exFAT
/dev/sdh2      1621014526  1953523711   166254593    5  Extended
/dev/sdh5   *  1820704768  1936750591    58022912   83  Linux
/dev/sdh6      1936752640  1953523711     8385536   82  Linux swap / Solaris
/dev/sdh7      1621014528  1820704767    99845120   83  Linux

Partition table entries are not in disk order

Disk /dev/sdg: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1              32    31266815    15633392    c  W95 FAT32 (LBA)

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x538cab66

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048  1936748543   968373248   83  Linux
/dev/sde2      1936748544  1953523711     8387584   82  Linux swap / Solaris
randell@randell-MS-7390:~$

---

