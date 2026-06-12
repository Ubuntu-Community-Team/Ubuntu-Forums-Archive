---
title: "dvd's are not seen"
date: 2008-03-28
forum: Multimedia &amp; Video
---

### Post by fibster on 2008-03-28
Hopefully someone has a fix for this. I have a compaq presario 2500 laptop that I just recently installed the beta 8.04  on. My dvd drive reads cd's but not dvd's? I have gone through the tutorial on installing everything to view a dvd movie, but still no luck wil not even recognize a dvd in the player? was wondering if I need to soft symlink? Anyway here is my basic fstab if anyone has any ideas?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=0db57e6e-7dc6-4ad6-a8f4-18718aa55492 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda5
UUID=53107a0d-54d3-4cc8-860b-f1b816449e53 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Thanks,

Todd aka Fibster

---

### Post by Yellow Pasque on 2008-03-28
Do you have a link for the tutorial you followed? Specifically, I was wondering if it got you setup with libdvdcss2 and other necessary "restricted" extras.
Also, could you post the output of this command (the part about your DVD drive)?:
```
sudo lshw -C disk
```

---

### Post by fibster on 2008-03-28
Thanks for the quick reply, I followed a link on this forum cant find it now but yes i installed everything. Any way here is the info u asked for.

Thank You,

 *-disk                  
       description: ATA Disk
       product: HITACHI_DK23EA-60
       vendor: Hitachi
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: 00K2A0A2
       serial: 4G7869
       size: 55GiB (60GB)
       capacity: 55GiB (60GB)
       capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
       configuration: apm=off mode=udma5 signature=ae32ae32 smart=on
  *-cdrom
       description: DVD writer
       product: AOPEN DVD RW ISU8484G
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: 1.11
       serial: TEMP_TV012_T7028
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
       configuration: mode=udma2 status=nodisc

---

### Post by Yellow Pasque on 2008-03-28
Ok, what program are you trying to use to view DVD's? (I like VLC myself). One thing to try  is opening your DVD program in a terminal and seeing the specific error messages it spits out when you put a DVD in.

---

