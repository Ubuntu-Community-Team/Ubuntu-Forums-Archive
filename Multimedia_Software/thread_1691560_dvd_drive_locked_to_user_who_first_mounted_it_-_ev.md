---
title: "dvd drive locked to user who first mounted it - even if they have logged out"
date: 2011-02-20
forum: Multimedia Software
---

### Post by versipellis on 2011-02-20
Hi,
I'm not sure if this is a generic problem with ubuntu or something to do with the set up on my machine. I haven't discovered any other posts about this issue, so I guess its something not many people experience...

Basically, once one user has mounted a dvd, no other users can access any  dvd's until the machine has been rebooted or the original user logs back in to unmount the dvd drive.  (If the original user is still logged in, other users will not even be able to reboot to sort this out).  Physically ejecting the drive and putting the dvd back in does not help.

This is causing my wife and daughter some annoyance, and if I can't sort it out I'll probably come under pressure to go back to Windows.  I really don't want to do that so any help would be appreciated.

Some extra info that may be useful...

Using Maverick Meerkat

**fstab contains** 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f5bf6238-3657-43c3-877c-f34edba32692 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=20a58db7-e039-4552-9a01-d940127a4513 none            swap    sw              0       0

after mounting, **mtab** contains (for example)

/dev/sda1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/dominic/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=dominic 0 0
/dev/sr0 /media/BBCDVD3068_A_DISC_1 udf ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077 0 0

---

