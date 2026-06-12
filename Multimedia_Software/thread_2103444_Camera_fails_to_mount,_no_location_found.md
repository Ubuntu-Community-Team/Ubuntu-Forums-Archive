---
title: "Camera fails to mount, no location found"
date: 2013-01-10
forum: Multimedia Software
---

### Post by oygle on 2013-01-10
This camera **doesn't** mount okay in Kubuntu 12.04. I can see it in Dolphin, copy pictures,etc, but when I try to go to the location /home/username/.gvfs/...etc,etc , it is not shown.

Where is the camera location in 12.04 ?

It's bus 4, device 2

```

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 06da:0002 Phoenixtec Power Co., Ltd UPS
Bus 002 Device 003: ID 03f0:8f11 Hewlett-Packard 
Bus 004 Device 002: ID 04a9:3149 Canon, Inc.

```

Oygle

---

### Post by Cheesemill on 2013-01-10
Try typing the command 'mount' into a terminal. This will list all of your devices along with the full path they are mounted on.

---

### Post by oygle on 2013-01-10
Hmm, ..maybe it isn't mounted properly ??

```

$ mount
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

```

---

### Post by Old_Grey_Wolf on 2013-01-10
Moved to Multimedia & Video at OP request.

---

### Post by oygle on 2013-01-10
If I put in a USB stick, it is mounted correctly ..

> 
$ **lsusb**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 06da:0002 Phoenixtec Power Co., Ltd UPS
[COLOR="Blue"]Bus 001 Device 005: ID 18a5:0243 Verbatim, Ltd[/COLOR]

$ **mount**
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
[COLOR="Blue"]/dev/sdb1 on /media/STORE N GO type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)[/COLOR]


Now if I plug in the camera and switch it on ..

> 
$ **lsusb**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 06da:0002 Phoenixtec Power Co., Ltd UPS
[COLOR="Blue"]Bus 001 Device 005: ID 18a5:0243 Verbatim, Ltd 
Bus 004 Device 007: ID 04a9:3149 Canon, Inc.[/COLOR]
 
$ **mount**
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
[COLOR="Blue"]/dev/sdb1 on /media/STORE N GO type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)[/COLOR]


In Dolphin, the USB stick shows in the LH pane/window as "STORE N GO", but the camera down't show in the LH pane, the contents only show in the RH pane.

I cannot 'navigate' to the camera location, it used to be (prior to 12.04) /home/username/.gvfs/..

How do I mount this camera properly ? It is a Canan Powershot A460 (PTP Mode)

Oygle

---

### Post by oygle on 2013-01-11
Have been searching a lot on the forums and Google, and this certainly is a problem with Canon camera's.

Looked where I store photos, and the file dates indicate that approx. 6 weeks ago, I was able to access /home/username/.gvfs/... for the photos.

What would have changed since ? Updates somewhere ?

Oygle

---

### Post by oygle on 2013-01-11
Lots more searching, and found a [post by "stafio"]("http://ubuntuforums.org/showpost.php?p=6891471&postcount=14")

> First, you need to install gphotofs through either synaptic or using apt-get. Create a directory in your home folder called "camera".
Mount using the command

```

gphotofs ~/camera

```

Unmount using

```

fusermount -u ~/camera

```

Have tested this a few times, works fine ..

Mount before attaching the Canon camera ..

```

$ **mount**
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

```

Mount using gphotofs

```

$ **gphotofs ~/camera**
$ **mount**
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

```

I was then able to browse the photos on the camera from ~/camera . Then unmount afterwards ..

```

$ **fusermount -u ~/camera**
$ 
$ **mount**
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

```

Oygle

---

