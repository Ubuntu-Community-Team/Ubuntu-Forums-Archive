---
title: "[SOLVED] Mythfrontend Dvd Mount issues"
date: 2008-11-08
forum: Mythbuntu
---

### Post by nrune on 2008-11-08
Trying to track down a dvd playback issue for sometime, I've hit a dead end and need some advice. 

With mythfrontend not running the dvd is automatically mounted and confirmed by a mount -l 

```
nrune@mythtv:/media$ sudo mount -l
/dev/hdc on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=nrune) [INDIANA_JONES_4_AC]
```

So then I run mythfrontend, and for some reason it unmounts the dvd 

```
nrune@mythtv:/media$ sudo mount -l
/dev/hda1 on / type ext3 (rw,relatime,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/hdb1 on /media/hdb1 type xfs (rw,noexec,nosuid,nodev) []
securityfs on /sys/kernel/security type securityfs (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)

```

So I figure hit eject and then reinsert the disk right? I get the same error.  
```
nrune@mythtv:/media$ sudo mount -l
/dev/hda1 on / type ext3 (rw,relatime,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/hdb1 on /media/hdb1 type xfs (rw,noexec,nosuid,nodev) []
securityfs on /sys/kernel/security type securityfs (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
```

So instead I ssh in to the myth box and use "sudo mount /dev/dvd" and bam disk is mounted and now plays in mythfrontend without problems. 

So this maybe a mounting or users rights issues I am not sure.  Any ideas? 

fstab:
```
 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=cf693595-a748-4792-8ace-b10e786f14c7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda5
UUID=54548e6f-0b23-4c72-b01d-fad8249eadfa none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#dev/hdb1
UUID=023d6c99-16d3-457c-9a2c-196f5c48c620 /media/hdb1    xfs  user,auto 0    0

```

Thanks in advance for any suggestions!

---

### Post by nrune on 2008-11-08
Nevermind solved my own issue.

had to comment out the /dev/hdc line in fstab and then change the location in mythbuntu media to /dev/hdc and it worked like a charm.  

Thanks

---

