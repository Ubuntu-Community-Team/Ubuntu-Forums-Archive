---
title: "Coby MP3 player"
date: 2009-11-12
forum: Multimedia Software
---

### Post by Nyken on 2009-11-12
Someone bought me this really nice looking mp3 player made by Coby. It mounts and I can look at what's on it like a thumb drive, but there are a couple of problems. When I try to drag and drop music to it or leave the folder and come back, Nautilus hangs. tried copying files from the command line, but it'll often hang.

Checked all the settings in fstab and mtab and tried a billion combinations of settings, but have yet to find the magic bullet to make this thing behave. It's a vfat drive. and I've set my fstab to rw and to sync, but no dice. Anyone know how to deal with a stubborn drive like this that doesn't involve a destroying a garbage disposal? I'm really loathe to drag out a spare computer I have and my old XP disc and made a windows computer just to run this thing - it comes with some kind of software suite that wine doesn't like to install.

copy of my mtab:

/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/panda/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=p$
/dev/sdb1 /media/NTFS fuseblk rw,nosuid,nodev,allow_other,default_permissions,b$
/dev/sdc /media/windows vfat rw,iocharset=utf8,umask=000 0 0

and my fstab, which shows some commented out stuff that I had tried:

## /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=f4a78ed1-dcec-44af-9a5f-9406c316aeff /               ext4    errors=remoun$
# swap was on /dev/sda5 during installation
UUID=2b1b225a-cae4-46e4-83ce-df3fa55e29b0 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sdc        /media/64B3-FAE1 vfat rw,nosuid,sync,nodev,uhelper=devkit,uid=$
#/dev/sdc        /media/64B3-FAE1 vfat rw,sync,uhelper=devkit,flush,uid=1000,gi$
#/dev/sdc        /media/64B3-FAE1 msdos   rw,sync,uid=1000,gid=1000   0     0
#/dev/sdc        /mnt/usb  vfat  rw,nosuid,sync  0 0
/dev/sdc  /media/windows/  vfat iocharset=utf8,umask=000  0    0




TIA!

---

### Post by Nyken on 2009-11-18
Decided to just take a hammer to it and smash it to bits. Feel much better now :D

---

### Post by kostkon on 2009-11-18
> **Nyken said:**
> Decided to just take a hammer to it and smash it to bits. Feel much better now :D
!!!!!!!!!!

---

### Post by Smartbreathanalyzer on 2009-11-18
Why would you smash it? 

[Alcohawk]("http://www.smartbreathalyzer.com/m1-AlcoHAWK.html")

---

### Post by Nyken on 2009-12-11
So did I - regret it, but it was satisfying.... wish I could still solve it.

---

### Post by Chronon on 2009-12-11
So. . . mark as solved (by hammer)?

---

### Post by Nyken on 2009-12-17
Aye... solved by hammer. Thus marked.

---

### Post by earthquakefish on 2009-12-17
Not sure if you want to know this.....!

But using xubuntu 8.10 and thunar I was able to load music onto my girlfriends Coby mp3 player....:)

---

