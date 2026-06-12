---
title: "CD Rom Will Not Mount"
date: 2009-05-10
forum: Multimedia Software
---

### Post by drazabyss on 2009-05-10
I have seen this indexed on google at various support boards.  There always seems to be a different solution or "the last upgrade fix it."  I just upgraded and it seemed to have caused the problem.

Simply, whenever I try to insert blank media (and I assume any media) into my CD ROM drive, I get massive errors.

First I had the problem of when booting with a CD in the drive, the desktop icons would not show, there was no access to folders, but I could run programs normally from the launchbar, etc.  I found [this]("http://ubuntuforums.org/showthread.php?t=1135678&page=2") thread, had the "ah ha!" moment of a CD being in the drive (who would think it?) and followed each of the last two pages of instructions (wrt brasero and lib permissions).

So my desktop icons/file browsing is ok now, but I now get the mounting error when trying to insert a CD.

The error is:

> Unable to mount Audio Disc  |  DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

When trying to mount in terminal:

> sudo mount /dev/scd0
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


> dmesg | tail
[ 3206.180349] end_request: I/O error, dev sr0, sector 1435608
[ 3206.181435] end_request: I/O error, dev sr0, sector 1436848
[ 3206.182552] end_request: I/O error, dev sr0, sector 1435600
[ 3206.183631] end_request: I/O error, dev sr0, sector 1248
[ 3206.184995] end_request: I/O error, dev sr0, sector 2496
[ 3206.186120] end_request: I/O error, dev sr0, sector 1248
[ 3206.187616] end_request: I/O error, dev sr0, sector 2496
[ 3206.187695] UDF-fs: No partition found (1)
[ 3206.224713] end_request: I/O error, dev sr0, sector 64
[ 3206.224800] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=f4b696e0-d31e-43d2-b424-b114ffaab8a6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=690111d3-2373-42b3-a9e5-3908a26a63fb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
//Colossus/public    /media/networkshare        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
# /dev/sdb1
UUID=2ED48130D480FB7B /media/windowsdrive ntfs defaults,umask=022,uid=1000 0 0

This is driving me a bit nuts-o :D  No DVD burned for my mother in-law for Mother's Day :(

Thanks in advance.

---

### Post by drazabyss on 2009-05-10
Ah, Jaunty, FWIW

---

### Post by drazabyss on 2009-05-11
.

---

### Post by drazabyss on 2009-05-11
Here's hwinfo outpud for cd-rom
> hwinfo --cdrom
17: SCSI 100.0: 10602 CD-ROM (DVD)                              
  [Created at block.247]
  UDI: /org/freedesktop/Hal/devices/storage_model_DVD__RW_ND_3450A
  Unique ID: KD9E.13nhWo0RC_1
  Parent ID: 3p2J.LYW64F5ou31
  SysFS ID: /class/block/sr0
  SysFS BusID: 1:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.1/host1/target1:0:0/1:0:0:0
  Hardware Class: cdrom
  Model: "_NEC DVD+-RW ND-3450A"
  Vendor: "_NEC"
  Device: "DVD+-RW ND-3450A"
  Revision: "103C"
  Driver: "ata_piix", "sr"
  Device File: /dev/sr0 (/dev/sg1)
  Device Number: block 11:0 (char 21:1)
  Features: CD-R, CD-RW, DVD, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+DL
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #7 (IDE interface)
  Drive Speed: 48


Any other info I can provide for troubleshooting help?

---

