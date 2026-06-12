---
title: "DVD media not recognized in 9.04"
date: 2010-10-16
forum: Multimedia Software
---

### Post by graeleight on 2010-10-16
I'm on ver 9.04. I have two DVD-RW drives. The system recognizes that I have them but when I put media into them it doesn't seem to realize I have done so with the following exception. If I boot with the media already in the drive it gets recognized and mounted. 

Once mounted the DVDs play perfectly. 

I do not have wubi installed.

When I try to use MOUNT I got the message: No media in drive.

---

### Post by P4man on 2010-10-16
Can you post the contents of

```
/etc/fstab
```

?
If there is a reference to /dev/scdX you can try commenting out that line.

---

### Post by graeleight on 2010-10-16
fstab:

[SIZE="1"]# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/SIZE]

I will try commenting out that /dev/scd1 line once I figure out how to get permission to do so. (i'm very new to ubuntu)

---

### Post by P4man on 2010-10-16
To edit that file, press Alt+F2 (or open a terminal) and run

```
gksudo gedit /etc/fstab
```

gedit is a texteditor, putting gksudo before opens it with root permissions. gksudo is for graphical applications (like gedit), sudo for terminal apps).

Anyway, change it like this:
```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/host/ubuntu/disks/root.disk / ext3 loop,errors=remount-ro 0 1
/host/ubuntu/disks/boot /boot none bind 0 0
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0
[COLOR="Red"]# [/COLOR]/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
```

See if that helps. 
BTW, why are you using 9.04 if you are new to ubuntu? 10.04 is the current LTS version, and 10.10 is just out.

edit: eeew.. you are using wubi.. me not like wubi.  If you are serious about using ubuntu, do a real install next time. And do not upgrade your current version of ubuntu to 10.04 or 10.10.

---

### Post by graeleight on 2010-10-16
I am actually NOT using wubi. I only mentioned it because I was trying to get help from the IRC channel and that was something someone asked me. I wanted to throw everything out that I had tried already.

I am on 9.04 because I installed a while back to play with and only starting using it as my primary OS last week (for more stable minecraft play)

I will probably upgrade soon.

However, I tried what you suggested and it worked like a charm!

Thanks a lot. 

I really need to start learning this OS. I'm a freaking IT professional this is embarassing. :-) (completely different platform)

---

### Post by P4man on 2010-10-16
that fstab is definitely from a wubi install. Look at the mount points, they all refer to virtual file systems on the windows host.

If this is indeed somehow not a wubi install; then did you try migrating from wubi and is this a leftover?

Can you post the output of

```

mount
```

---

### Post by graeleight on 2010-10-16
mount:

/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sdb1 on /host type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-19-generic/volatile type tmpfs (rw,mode=755)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mike/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mike)
/dev/sr0 on /media/GILMORE_GIRLS_S6_D5 type udf (ro,nosuid,nodev,uhelper=hal,uid=1000)

When I was first asked about if I was using wubi I had to reboot back to my windows partition and look. When I was testing different linux flavors a couple of years ago I remembered using wubi for at least one of them but couldn't remember which. So I checked and it wasn't installed anymore. However from what you are saying it must have been Ubuntu after all and I must have migrated or something.

When I upgrade I'll do a full install.

---

### Post by alf2 on 2010-10-18
I have a disc cd that is not recognised and wont work, it used to.
I have a lg dvd that open and closes and reads disks but wont boot a disk.
I have a freecom external dvd that reads disks but wont boot a disk.
Now remember!! I'm a complete novice at linux of any sort so, how do I 
a: Get the two disks on the computer to work correctly and also the external disk to work correctly.
Or do I throw the computer in the bin?

---

