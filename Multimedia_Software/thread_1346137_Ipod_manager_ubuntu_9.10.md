---
title: "Ipod manager ubuntu 9.10"
date: 2009-12-04
forum: Multimedia Software
---

### Post by De Kleine on 2009-12-04
I just installed ubuntu 9.10 and I'm trying to get an Ipod-manager working but gtkpod doesn't seem to notice that my Ipod is there (if i click on load Ipod it doesn't do anything) and I tried to install yamipod but that program doesn't open at all (I copied the libfmodex file to the          /usr/lib folder. 
Can anyone help me (but please use 'normal language' I yust started here;))

---

### Post by Bigtime_Scrub on 2009-12-04
What kind of ipod are you using? Also, does your computer detect the iPod? Does it mount automatically? Do you see a little ipod icon on your desktop when you plug it in. When it is plugged in please post the output of ```
sudo mount
```

---

### Post by De Kleine on 2009-12-05
I'm using a Ipod Classic (6th generation) and I can see the Ipod icon when  I plug it in. I can also browse through my Ipod in rythmebox.

sudo mount gives the following output

> /dev/loop0 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda2 on /host type fuseblk (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/poulsteenbeek/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=poulsteenbeek)
/dev/sda3 on /media/Data type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1 on /media/IPOUL type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


---

