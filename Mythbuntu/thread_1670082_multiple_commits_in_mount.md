---
title: "multiple commits in mount"
date: 2011-01-18
forum: Mythbuntu
---

### Post by ian dobson on 2011-01-18
Hi,

After upgrading my frontend to a ssd I've noticed that the drive seems to be accessed more other than I'd expect. Looking in fstab I see:-

```

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system>                           <mount point> <type> <options>                                                          <dump>  <pass>
proc                                      /proc         proc  defaults                                                               0       0
# /dev/sda1
UUID=671953de-a48b-464e-ac26-1707715287bf /             ext4  discard,noatime,nodiratime,errors=remount-ro,data=writeback,commit=30  0       0
/dev/scd0                                 /media/cdrom0       udf,iso9660 user,noauto,exec,utf8                                      0       0
/dev/sda2                                 /mytharchive  ext4  noatime,nodiratime,errors=remount-ro,data=writeback,discard,commit=30  0       0

```

when I type mount from the command line I see:-
mount
**/dev/sda1 on / type ext4 (rw,noatime,nodiratime,discard,errors=remount-ro,data=writeback,commit=30,commit=0)**
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
**/dev/sda2 on /mytharchive type ext4 (rw,noatime,nodiratime,errors=remount-ro,data=writeback,discard,commit=30,commit=0)**

Why am I seeing commit=30,commit=0? and does the kernel/ext4 fs use 0seconds or 30 seconds for the write delay?

Regards
Ian Dobson

---

### Post by ian dobson on 2011-01-19
Hi,

OK, this looks like a bug in mountall when called from upstart/init scripts.

If I just all mountall after the system has booted the the commit=0 vanishes :confused:

Regards
Ian Dobson

---

