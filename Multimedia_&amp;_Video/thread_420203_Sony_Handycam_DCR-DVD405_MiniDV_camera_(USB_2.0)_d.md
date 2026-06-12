---
title: "Sony Handycam DCR-DVD405 MiniDV camera (USB 2.0) dismounts"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by raptor2552 on 2007-04-23
I can read/write/copy/cut still pictures from this devices memory stick without any problems. However, when I connect the camera to retrieve video the camera mounts, an icon appears on the desktop as SONY_MOBILE (/dev/scd0 on /media/cdrom1 type iso9660 (ro,noexec,nosuid,nodev,user=mike)) then dismounts after a few seconds and ejects the disk. The video starts to play but of course stops after the device is dismounted. The OS is Feisty 7.04 up to date. Anyone have any thoughts, cures, file that needs to be edited?

mike in /media:$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-386/volatile type tmpfs (rw)
/dev/sda2 on /media/DataVolume type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda1 on /media/WindowsVolume type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/scd0 on /media/cdrom1 type iso9660 (ro,noexec,nosuid,nodev,user=mike)

---

