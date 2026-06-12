---
title: "DVD-RW not working"
date: 2009-01-05
forum: Multimedia Software
---

### Post by mern1 on 2009-01-05
Just recently installed 8.10 and am unable to get my dvdrw drive to work.  With a CD in the drive it says it cannot be mounted (no media in the drive). Any help would be greatly appreciated as I don't really have a clue what I'm doing.  Thanks

Results from lshw -C disk:

 ```
*-cdrom:0               
       description: DVD-RAM writer
       product: DVDRW SHM-165H6S
       vendor: LITE-ON
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: HS0D
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
  *-cdrom:1
       description: CD-R/CD-RW writer
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/scd1
       logical name: /dev/sr1
       capabilities: audio cd-r cd-rw
       configuration: status=nodisc
  *-disk:0
       description: ATA Disk
       product: WDC WD2500KS-00M
       vendor: Western Digital
       physical id: 0
       bus info: scsi@8:0.0.0
       logical name: /dev/sda
       version: 02.0
       serial: WD-WCANK1507472
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=52685268
  *-disk:1
       description: ATA Disk
       product: WDC WD1001FALS-0
       vendor: Western Digital
       physical id: 1
       bus info: scsi@9:0.0.0
       logical name: /dev/sdb
       version: 05.0
       serial: WD-WMATV0374195
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=5e378cc5
 
```

fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ed815082-ef9c-4e93-90a4-409f4f584987 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=4908b1d5-ef40-4220-bdad-64ef568f9ce3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sdb1 
UUID=2C6827E96827B08E /media/Shared   ntfs-3g  ro,auto,user,fmask=0111,dmask=0000 0 0

```

---

### Post by dreamingdarkness on 2009-01-27
I have a similar but not exactly the same issue as the OP. Not trying to post-jack, just consolidate!

My DVD/CD RW drive will detect initially and mount to the desktop and places menu, but any attempts to access it with any program will lead to it de-mounting.
I think it believes itself to be open, but it won't respond to anything except a quick reboot into my Windows partition where it behaves itself. 


Below are the relevant areas (as far as I can tell) of lshw and fstab. 

```
           *-cdrom 
                description: DVD-RAM writer 
                physical id: 1 
                bus info: scsi@1:0.0.0 
                logical name: /dev/scd0 
                logical name: /dev/sr0 
                capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram 
                configuration: status=open 


fstab:
# /etc/fstab: static file system information. 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1 
/host/ubuntu/disks/boot /boot           none    bind            0       0 
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0 

```

---

