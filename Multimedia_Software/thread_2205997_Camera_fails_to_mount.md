---
title: "Camera fails to mount"
date: 2014-02-16
forum: Multimedia Software
---

### Post by oygle on 2014-02-16
The thread at [http://ubuntuforums.org/showthread.php?t=2103444](http://ubuntuforums.org/showthread.php?t=2103444) was my solution until today. For some strange reason, the camera fails to mount properly.

~/camera$ **gphotofs ~/camera**
fusermount: failed to open /etc/fuse.conf: Permission denied
fusermount: failed to access mountpoint /home/username/camera: Permission denied

**mount**
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
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
/dev/sda3 on /home type ext3 (rw)
gvfs-fuse-daemon on /home/username/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=username)
gphotofs on /home/username/camera type fuse.gphotofs (rw,nosuid,nodev,user=username)

---

### Post by oygle on 2014-02-18
bump

---

