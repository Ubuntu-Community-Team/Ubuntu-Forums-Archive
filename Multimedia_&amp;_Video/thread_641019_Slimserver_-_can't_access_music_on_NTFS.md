---
title: "Slimserver - can't access music on NTFS"
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by jason442 on 2007-12-14
ey folks,

I having a weird issue with Slimserver. Slimserver is installed and running. For some reason I cannot set the music folder to my NTFS drive - which contains all my music. It's mounted at /media/sdc5/Music. slimserver says "ops - "/media/sdc5/Music" doesn't seem to be a valid directory. Try again.

I can browse to that location and also play music using the default ubuntu media player. So what's the deal?

I did a search and found somebody with the same problem...but I did not see a solution.

here is my fstab file:
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=ef957c9a-4c77-493c-8e9a-d550732d741c / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1
UUID=16F84F77F84F5461 /media/sda1 ntfs defaults,umask=007,gid=46 0 1
# /dev/sdb1
UUID=BD45E74BF382FD95 /media/sdb1 ntfs defaults,umask=007,gid=46 0 1
# /dev/sdc5
UUID=684F9B48F1CF5917 /media/sdc5 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda3
UUID=df94e11e-1201-479a-864f-e496df528d53 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0



Please help!
Thanks!
Jason

---

