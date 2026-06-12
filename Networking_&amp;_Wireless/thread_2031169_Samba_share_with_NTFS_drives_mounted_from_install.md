---
title: "Samba share with NTFS drives mounted from install?"
date: 2012-07-21
forum: Networking &amp; Wireless
---

### Post by thumbs88 on 2012-07-21
Hello I'm new here and I did search the forums beforehand but I didn't see anything that really fit what I was having problems with so if it was answered already I'm sorry...

Here's what I have:

I just installed Ubuntu 12.04 and I have 4 extra data drives (all NTFS) I mounted them at the time of install so I didn't need to edit fstab but I guess I was wrong lol

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=57a14cb2-80d3-432c-8d67-a09c66ae7df1 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=70F1-AC7B  /boot/efi       vfat    defaults        0       1
# /media/15 was on /dev/sdc1 during installation
UUID=2F98FF8D124B0EAD /media/15       ntfs    defaults,umask=007,gid=46 0       0
# /media/15_ was on /dev/sdd1 during installation
UUID=DA2CCA5F2CCA3673 /media/15_      ntfs    defaults,umask=007,gid=46 0       0
# /media/20 was on /dev/sdb1 during installation
UUID=20B5ED0D2F7DB391 /media/20       ntfs    defaults,umask=007,gid=46 0       0
# /media/20_ was on /dev/sde1 during installation
UUID=18F41FBAF41F98D8 /media/20_      ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda2 during installation
UUID=024cb637-1dc2-4fb0-993a-3cc74d3885aa none            swap    sw              0       0

```

I want to be able to share the extra drives (/media/20 /media/15... etc) with SAMBA but when I right-click share on say /media/15 and allow guests and writes to the dive I get the error ```
Could not change the permissions of folder "15"
```
I was wondering if anyone else had this issue and had a fix?

---

### Post by Morbius1 on 2012-07-21
> UUID=2F98FF8D124B0EAD /media/15       ntfs    defaults,umask=007,gid=46 0       0You will never be able to create a true anonymous guest share from a partition mounted that way. That will mount with root as owner but accessible to anyone in the plugdev ( gid=46 ) group. The anonymous guest is not a member of the plugdev group. Anyway, you can't change ownership or permissions after the mount on an NTFS partition so you will need to change how you are mounting it:

Change it to this:
```
UUID=2F98FF8D124B0EAD /media/15 ntfs defaults,umask=000 0       0
```[COLOR=Blue]OR[/COLOR], You can change it to this so you can create a share in Nautilus from your own user name:
```
UUID=2F98FF8D124B0EAD /media/15 ntfs defaults,umask=000,uid=1000 0       0
```Then unmount the partition:
```
sudo umount /media/15
```And remount it this way so it checks for any typos you may have made:
```
sudo mount -a
```

---

### Post by thumbs88 on 2012-07-21
> **Morbius1 said:**
> You will never be able to create a true anonymous guest share from a partition mounted that way. That will mount with root as owner but accessible to anyone in the plugdev ( gid=46 ) group. The anonymous guest is not a member of the plugdev group. Anyway, you can't change ownership or permissions after the mount on an NTFS partition so you will need to change how you are mounting it:

Change it to this:
```
UUID=2F98FF8D124B0EAD /media/15 ntfs defaults,umask=000 0       0
```[COLOR=Blue]OR[/COLOR], You can change it to this so you can create a share in Nautilus from your own user name:
```
UUID=2F98FF8D124B0EAD /media/15 ntfs defaults,umask=000,uid=1000 0       0
```Then unmount the partition:
```
sudo umount /media/15
```And remount it this way so it checks for any typos you may have made:
```
sudo mount -a
```

Thank you this worked perfectly!!

---

