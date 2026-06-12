---
title: "Tovid"
date: 2013-01-31
forum: Multimedia Software
---

### Post by izombie666 on 2013-01-31
I have three drives on my computer.  a 64GB solid state, a 500gb seagate hybrid and a 1tb external. all my software runs on the SSD and the other two are storage.   I store my audio and video files in the external drive.  How do I get TOVID to see my external drive and my 500gb drive?

---

### Post by George Heine on 2013-02-21
> I have three drives on my computer.  a 64GB solid state, a 500gb seagate  hybrid and a 1tb external. all my software runs on the SSD and the  other two are storage.   I store my audio and video files in the  external drive.  How do I get TOVID to see my external drive and my 500gb drive?Are you running command-line tovid?  
Open a terminal (<Ctl><Alt>T) and type
```
mount
```and you will see a list of entries like
```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
...
/dev/sdb1 on /media/MOUNT_POINT  type ext3 (rw,nosuid,nodev,uhelper=udisks)
```Your external drives will be likely at the end of the list.  The "MOUNT_POINT" will be either the device label or the device UUID (unless you have configured it to be something else.)

You can either go to the mounted device and run tovid there:
```
cd /media/MOUNT_POINT/LOCATION_OF_VIDEOS
tovid [menu|xml|dvd] {options}
```or,  to save writing to the device, you can create "symbolic links" to the video files on the device:
```
ln -s /media/MOUNT_POINT/LOCATION_OF_VIDEOS/video1.mpg
ln -s /media/MOUNT_POINT/LOCATION_OF_VIDEOS/video2.mpg
...
```You can then run  tovid directly on the link files in your SSD.  You should also be able to run tovid gui on them.

HTH -

---

