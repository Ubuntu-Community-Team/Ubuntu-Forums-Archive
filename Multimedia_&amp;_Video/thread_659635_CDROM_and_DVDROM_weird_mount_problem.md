---
title: "CDROM and DVDROM weird mount problem"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by Hawk__0 on 2008-01-05
I have 2 removable disc drives in my system:
1. CD-RW/DVD player: Connected Via IDE
2. DVD-RW/DVD player: Connected Via SATA

Whenever I insert something into my DVDRW it cant mount.  I can burn things with it just fine, but it wont mount.  The CD-RW will mount them.

My main concern here is how I cant use the dd command.  I'm trying to make an ISO but I get I/O errors:

```
steve@steve:/media$ sudo dd if=/dev/cdrom of=anisofile.iso
dd: reading `/dev/cdrom': Input/output error
40+0 records in
40+0 records out
20480 bytes (20 kB) copied, 0.139546 seconds, 147 kB/s
steve@steve:/media$ sudo dd if=/dev/dvd of=anisofile.iso
dd: reading `/dev/dvd': Input/output error
40+0 records in
40+0 records out
20480 bytes (20 kB) copied, 0.109219 seconds, 188 kB/s

```

In /dev I have the following:
cdrom
cdrom2
dvd
dvd2
dvdrw2

I Tried using every one of those while having the CD in both drives, and I get the same errors as seen above.  Anybody know how to fix this?

---

### Post by yabbadabbadont on 2008-01-05
It isn't an audio cd is it?  They don't contain a real filesystem and have to be duplicated using other means.

---

### Post by Hawk__0 on 2008-01-06
No, its anything. software, games, movies, etc.

---

### Post by yabbadabbadont on 2008-01-06
Strange.  I've heard of people having issues with SATA CD/DVD drives, but not ones connected through the IDE channel.  Which kind of matches your experience with mounting, but it doesn't jive with trying to create an ISO from the IDE connected drive.  What is truly bizarre, is that they both fail after 20kb.  The only thing I can suggest to try to track this down, is to check the output of dmesg, right after you repeat the error.  Maybe there will be a more descriptive error message there.  You might also try using k3b (or whichever burning software you prefer) to create the ISO.  It would be interesting to see if you get the same error.

---

### Post by Hawk__0 on 2008-01-06
I tried K3B already, it still had errors.  here is the exact error output:
(BTW this is the same error regardless of which drive I use)
```
System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
TSSTcorp CDDVDW SH-S203B SB01 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

LITE-ON COMBO SOHC-5232K NK0A (/dev/hdd, ) [CD-R, CD-RW, CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]
K3bDataTrackReader
-----------------------
reading sectors 0 to 232765 with sector size 2048. Length: 232766 sectors, 476704768 bytes.
using buffer size of 12 blocks.
Problem while reading. Retrying from sector 12.
Read error in sector 12.
Read a total of 12 sectors (24576 bytes)


```

and here's a screenshot:
[IMG]http://img116.imageshack.us/img116/3907/k3berrorgh3.png[/IMG]
EDIT: This is the same with 3 different CD's I tried.

---

### Post by Hawk__0 on 2008-01-06
bump

---

### Post by Yellow Pasque on 2008-01-06
post your /etc/fstab file.

Also, see if you can post:
```
sudo lshw -C disk
```

---

### Post by Hawk__0 on 2008-01-06
```
steve@steve:~$ sudo lshw -C disk
[sudo] password for steve:
  *-disk:0                
       description: ATA Disk
       product: Maxtor 6Y160L0
       vendor: Maxtor
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: YAR41BW0
       serial: Y458G49E
       size: 152GB
       capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
       configuration: apm=off mode=udma6 smart=on
  *-disk:1
       description: ATA Disk
       product: ST3250824A
       vendor: Seagate
       physical id: 1
       bus info: ide@0.1
       logical name: /dev/hdb
       version: 3.AAD
       serial: 4ND1P2JB
       size: 232GB
       capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
       configuration: mode=udma5 smart=on
  *-cdrom
       description: DVD reader
       product: LITE-ON COMBO SOHC-5232K
       physical id: 1
       bus info: ide@1.1
       logical name: /dev/hdd
       version: NK0A
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
       configuration: mode=udma2 status=nodisc
  *-cdrom
       description: DVD-RAM writer
       product: CDDVDW SH-S203B
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@7:0.0.0
       logical name: /dev/cdrom2
       logical name: /dev/dvd2
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: SB01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
  *-disk
       description: SCSI Disk
       product: StorageVault HD
       vendor: OEI-USB2
       physical id: 0.0.0
       bus info: scsi@8:0.0.0
       logical name: /dev/sda
       version: 1.19
       serial: WD-WCAL75665433
       size: 232GB
       capabilities: partitioned partitioned:dos
steve@steve:~$ 


```

```
steve@steve:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=3d27f7f0-c4a3-4045-a629-9dd45b80cbe0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=548ac3b6-c02f-49e0-a81c-7547f76fef4a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
steve@steve:~$ 


```

```
steve@steve:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=3d27f7f0-c4a3-4045-a629-9dd45b80cbe0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=548ac3b6-c02f-49e0-a81c-7547f76fef4a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
steve@steve:~$ cat /etc/mtab
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
steve@steve:~$ 


```

---

### Post by Yellow Pasque on 2008-01-06
Open /etc/fstab with sudo gedit and change this:
```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```
to this:
```
**/dev/scd0**   /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

It won't take effect until you restart, but you can use the following command to mount a DVD disc if you don't want to restart:
```
mount -t udf /dev/scd0 /media/cdrom0
```

---

### Post by Hawk__0 on 2008-01-07
ok thanks, I did that but it wont mount properly:
```
steve@steve:~$ sudo mount -t udf /dev/scd0 /media/cdrom0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

steve@steve:~$ ls /media/cdrom0
steve@steve:~$ 

```

there is a disc in the drive, but nothing is listed when I ls the directory.

---

### Post by Hawk__0 on 2008-01-08
bump

---

### Post by mc4man on 2008-01-08
with in all the info you've posted are some odd things. Would be good to know how is your dvd writer connected,  - into a sata controller on mobo or into a sata card

---

### Post by Hawk__0 on 2008-01-08
I hooked up this dvd burner AFTER ubuntu was already installed... if that helps.. and i was already having some strange issues before as well.

My burner is connected to the first of my 6 onboard sata ports.  I have an asus a8n-sli deluxe mobo.

---

### Post by Hawk__0 on 2008-01-08
bump

---

### Post by kens8 on 2008-01-19
You can probably find the answer here: [ http://linux.developers.dk/ich8m/]("http://linux.developers.dk/ich8m/")

---

