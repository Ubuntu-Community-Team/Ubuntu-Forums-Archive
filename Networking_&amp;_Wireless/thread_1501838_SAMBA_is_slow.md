---
title: "SAMBA is slow"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by ubunterooster on 2010-06-04
Slower than dial-up even. Fstab below ```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0ce98116-d3d2-4233-9868-1432f691722d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=1a00cf8d-ce46-408d-8cc3-1cac8edfb6e7 none            swap    sw              0       0
/dev/sdb1  /media/2TB  auto  auto,user,exec,rw  0  
```

---

### Post by madverb on 2010-06-04
What does your fstab have to do with Samba?

---

### Post by ubunterooster on 2010-06-04
A wild (and tired) guess, (nothing more) that the automounting of the  shared ext4 drive (sdb1) may *somehow* be related. 

In short I've no idea where to begin, seeing scroogle and UF searches have failed me.

---

### Post by ubunterooster on 2010-06-08
???

---

### Post by ubunterooster on 2010-06-11
Solved by Trying Mint after reinstalls of Ubuntu failed

---

