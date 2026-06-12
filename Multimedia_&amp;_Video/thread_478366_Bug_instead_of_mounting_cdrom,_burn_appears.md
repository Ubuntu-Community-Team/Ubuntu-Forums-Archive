---
title: "Bug? instead of mounting cdrom, burn:/// appears"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by allanvaliati on 2007-06-19
When I insert a media in the drive, ubuntu does not mount it correctly. Instead of it, nautilus open the location 
burn:///. In Mandriva it always worked as should be. 

This is mine fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=5c26022a-7fce-461d-8386-c280d16495bc /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=2c3e987b-92ef-4a5c-bd4a-8c2ddbd0b858 /media/hda1     ext3    defaults        0       2
# /dev/hda4
UUID=a2149fb8-4006-4d83-9d6e-40a03ec33ef5 /media/hda4     ext3    defaults        0       2
# /dev/hda2
UUID=937c76a7-d1a3-4a99-9a63-82e22509751b none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Is it a ubuntu bug ?

---

### Post by thelinuxguy on 2007-06-19
Does it happen when you insert a blank disk? Or any disk?

If it happens only for blank disks, try this:
System >> preferences >> Removable drives and media >> Storage 
Uncheck "Burn a CD or DVD when a blank disk is inserted".

---

