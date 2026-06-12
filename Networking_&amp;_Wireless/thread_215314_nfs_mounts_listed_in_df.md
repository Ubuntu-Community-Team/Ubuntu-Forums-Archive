---
title: "nfs mounts listed in df?"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by Dubbayoo on 2006-07-13
Do nfs mounts list in df output? I thought they did but mine aren't. 

steve@ubu:/data/ipod/Music$ **df -h**
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              33G  4.2G   28G  14% /
varrun                759M  116K  759M   1% /var/run
varlock               759M  4.0K  759M   1% /var/lock
udev                  759M  168K  759M   1% /dev
devshm                759M     0  759M   0% /dev/shm
lrm                   759M   18M  742M   3% /lib/modules/2.6.15-25-686/volatile
/dev/hda1             231G  110G  110G  51% /data
/dev/sdb2             3.8G  3.6G  133M  97% /media/ipod


steve@ubu:/data/ipod/Music$ **cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /data           ext3    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# added by me
jeeves:/home    /mnt/home       nfs     rw,hard,rsize=8192,wsize=8192,timeo=14,intr     0       0
jeeves:media    /mnt/music      nfs     rw,hard,rsize=8192,wsize=8192,timeo=14,intr     0       0


steve@ubu:/data/ipod/Music$ **sudo mount -a**
mount: jeeves:/home already mounted or /mnt/home busy
mount: jeeves:media already mounted or /mnt/music busy

---

### Post by nick58b on 2006-07-15
My NFS mounts were visible in df up until the 2.6.15-26 kernel update. I'm not sure what changed.

---

