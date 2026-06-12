---
title: "amarok and secondary hard drive dont get along"
date: 2008-05-09
forum: Multimedia Software
---

### Post by hatchet_lips on 2008-05-09
im not entirely sure where to ask these questions, so forgive me if ive picked the wrong outlet.

i have a rather large music collection and i keep it on a secondary IDE drive.  i can access this drive by going Places>Computer>Secondary Drive.  when i boot though, this drive is not mounted and i first have to access it to mount it.

obviously amarok cant find the files until the drive is mounted, so is there a way to have my secondary drive mount up when i boot ubuntu?  id rather not go through the process of accessing it everytime and then loading up amarok just to hear some tunes.

secondly, im curious if im able to listen to the shoutcast and hypemachine streams through amarok, and if so, how would i go about doing so?  this is more about amarok than ubuntu, so i know its in the wrong forums, but its related at least.

any help is greatly appreciated!

---

### Post by scragar on 2008-05-09
After mounting your driver run ```
mount
``` and post output back here, I'll help you edit your fstab so your second HD automounts.

go: Playlist > add stream, then put in the URL of the podcats RSS feed.

---

### Post by hatchet_lips on 2008-05-09
heres what terminal tells me after ive just mounted my secondary drive.


bp@bp-desktop:~$ mount
/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bp/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bp)
/dev/scd0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=bp)
/dev/sda1 on /media/chuck type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


just a heads up, none of what i just posted makes sense to me.

---

### Post by scragar on 2008-05-10
```
sudo gedit /etc/fstab
```
go down to the bottom and add this line:
```
/dev/sda1	/media/chuck     auto    defaults        0       2
```

then just double check that the directory exists:```
sudo mkdir /media/chuck
```


Drive should automount now.

---

