---
title: "Nothing happens after inserting VCD in my DVD drive (CD not detected)"
date: 2012-11-26
forum: Multimedia Software
---

### Post by amitst on 2012-11-26
When I insert any VCD into my DVD drive, it spins for half a minute and then nothing happens.

I was able to play this VCD on my Win7 laptop.

Also if I insert any DVD in Ubuntu then it plays fine. So DVD drive is working fine.

After inserting VCD I tried the following things,
* Through VLC selected Media->Open Disc->VCD (tried with various track numbers)
  * Also tried with devices as /dev/cdrom /dev/sr0
* Tried mounting through mount command
$ sudo mount -t iso9660 /dev/sr0 /media/cdrom
mount: no medium found on /dev/sr0

I figured out that /dev/sr0 must be my CD-ROM through the dmesg command.
$ dmesg | grep CD
[    0.902222] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7200A  1.06 PQ: 0 ANSI: 5
[    0.904686] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.904864] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    2.560435] scsi 7:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 0
[    2.582577] sr 7:0:0:0: Attached scsi CD-ROM sr1

The sr1 is actually a USB stick.

Any pointers?

Here is my Ubuntu version,
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise

---

### Post by BicyclerBoy on 2012-11-26
The linux VCD XCD support had problems with Form2 file format..

Does this work ?
mount -t cdfs -o ro /dev/sr0 /media/cdrom

less /proc/cdfs

I've never laid hands on a VCD, so hard to help.

---

### Post by amitst on 2012-11-27
There is no cdfs option for mount. Tried the following and other options as well. These are the main errors I am getting.
$ sudo mount -t adfs -o ro /dev/sr0 /media/cdrom
mount: no medium found on /dev/sr0
$ sudo mount -t cifs -o ro /dev/sr0 /media/cdrom
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Here is the man page section that describes the types supported,

            The argument following the -t is used to indicate the filesystem
              type.   The  filesystem  types  which  are  currently  supported
              include:  adfs,  affs,  autofs,  cifs,  coda,  coherent, cramfs,
              debugfs, devpts, efs, ext, ext2, ext3, ext4, hfs, hfsplus, hpfs,
              iso9660,  jfs, minix, msdos, ncpfs, nfs, nfs4, ntfs, proc, qnx4,
              ramfs, reiserfs, romfs, squashfs,  smbfs,  sysv,  tmpfs,  ubifs,
              udf,  ufs,  umsdos,  usbfs,  vfat, xenix, xfs, xiafs.  Note that
              coherent, sysv and xenix  are  equivalent  and  that  xenix  and
              coherent  will be removed at some point in the future &#8212; use sysv
              instead. Since kernel version 2.1.21 the types ext and xiafs  do
              not  exist anymore. Earlier, usbfs was known as usbdevfs.  Note,
              the real list of all supported filesystems depends on your  ker&#8208;
              nel.

---

### Post by amitst on 2012-11-27
There is no cdfs option for mount. Tried the following and other options as well. These are the main errors I am getting.
$ sudo mount -t adfs -o ro /dev/sr0 /media/cdrom
mount: no medium found on /dev/sr0
$ sudo mount -t cifs -o ro /dev/sr0 /media/cdrom
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Here is the man page section that describes the types supported,

            The argument following the -t is used to indicate the filesystem
              type.   The  filesystem  types  which  are  currently  supported
              include:  adfs,  affs,  autofs,  cifs,  coda,  coherent, cramfs,
              debugfs, devpts, efs, ext, ext2, ext3, ext4, hfs, hfsplus, hpfs,
              iso9660,  jfs, minix, msdos, ncpfs, nfs, nfs4, ntfs, proc, qnx4,
              ramfs, reiserfs, romfs, squashfs,  smbfs,  sysv,  tmpfs,  ubifs,
              udf,  ufs,  umsdos,  usbfs,  vfat, xenix, xfs, xiafs.  Note that
              coherent, sysv and xenix  are  equivalent  and  that  xenix  and
              coherent  will be removed at some point in the future — use sysv
              instead. Since kernel version 2.1.21 the types ext and xiafs  do
              not  exist anymore. Earlier, usbfs was known as usbdevfs.  Note,
              the real list of all supported filesystems depends on your  ker&#8208;
              nel.

---

### Post by BicyclerBoy on 2012-11-27
It seems cdfs as a separate package had stopped at kernel 2.6.27..maybe it was included into std kernel filesystem support..

Sorry, don't know.

---

### Post by amitst on 2012-11-28
No problem. Thanks for all the support.

---

