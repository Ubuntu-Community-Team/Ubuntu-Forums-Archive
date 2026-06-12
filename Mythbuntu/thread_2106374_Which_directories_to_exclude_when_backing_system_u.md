---
title: "Which directories to exclude when backing system up with grsync?"
date: 2013-01-18
forum: Mythbuntu
---

### Post by km782 on 2013-01-18
I have spent a lot of time setting up my Mythbox and I want to back it up in case of a hard drive failure or an update breaks something.  Honestly if I had to start over I don't know if I could get it back the way it is now.  I'm not afraid of the command line but I'm also far from a Linux wiz.  

Anyways, I was hoping to use grsync to backup my entire system.  This way if anything at all goes wrong I can restore it to exactly the way it was before.  I am going to exclude my recordings and videos so I can save disk space (my hard drive is 2 tb) and I don't really care if they end up being lost.  Everything else (drivers, firmware, program installations, settings, database, etc.) I want to easily be able to restore.  Other than the ones that I've listed below are there any other directories that I can exclude that take up significant space?  Thanks

/var/lib/mythtv/livetv
/var/lib/mythtv/recordings
/var/lib/mythtv/videos

---

### Post by SeijiSensei on 2013-01-19
/proc, /sys, /run, and /dev should be excluded as well.  They are not actually stored on your disk but created by the kernel at boot.  My 12.04 system lists these if I run "mount":

```

proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)

```

Notice that none of these are on the hard drive (e.g., /dev/sda1).

---

### Post by km782 on 2013-01-19
> **SeijiSensei said:**
> /proc, /sys, /run, and /dev should be excluded as well.  They are not actually stored on your disk but created by the kernel at boot.  My 12.04 system lists these if I run "mount":

Notice that none of these are on the hard drive (e.g., /dev/sda1).

Great, thank you!  I've been playing around with the simulation mode in grsync and I came across a few more directories that I'm wondering about (my login is htpc):

/home/htpc/.local/share/Trash     (263mb)
/home/htpc/.cache/chromium/Default/Cache      (143mb)
/home/htpc/.mythtv/themecache    (1.4gb)
/home/htpc/.mythtv/remotecache    (196mb)
/var/cache         (256mb)

The total size for my backup is about 9gb right now.  Would any of these be dangerous to exclude?  In other words, if I start from scratch and restore my system would it still function if these directories were empty?  Thanks again for the help!

---

