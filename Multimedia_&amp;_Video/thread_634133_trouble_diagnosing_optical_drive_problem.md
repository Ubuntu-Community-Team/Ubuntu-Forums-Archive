---
title: "trouble diagnosing optical drive problem"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by lej on 2007-12-07
Used 6.06 for quite awhile now.. a few months back I noticed that it wasn't playing audio cds anymore... haven't been bothered by it too much and I was planning to do a fresh install for gutsy anyway... have now done a fresh install expecting the issue to resolve itself, but the same situation exists where the system can mount all other discs but can't read the audio ones... a few details posted below:

Drive:

Lite-On dvd/cd rewritable   model: SHW-1635S

etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f4000f49-0df2-4c3a-ba69-9155795e80db /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0cf03fd5-963e-4307-97be-4f6ae078baba none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,auto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

greps:

cano@cano-desktop:~$ ls -l /dev | grep dvd
lrwxrwxrwx 1 root   root           3 2007-12-07 14:50 dvd -> hdd
lrwxrwxrwx 1 root   root           3 2007-12-07 14:50 dvdrw -> hdd
cano@cano-desktop:~$ ls -l /dev | grep cd
lrwxrwxrwx 1 root   root           3 2007-12-07 14:50 cdrom -> hdd
lrwxrwxrwx 1 root   root           3 2007-12-07 14:50 cdrw -> hdd
brw-rw---- 1 root   cdrom    22,  64 2007-12-07 14:49 hdd
crw-rw-rw- 1 root   tty       2, 221 2007-12-07 14:49 ptycd
crw-rw-rw- 1 root   tty       3, 221 2007-12-07 14:49 ttycd

PS there is an analog cable from the drive to the motherboard that I noticed was unplugged after the gutsy install (I've since plugged it in)

---

