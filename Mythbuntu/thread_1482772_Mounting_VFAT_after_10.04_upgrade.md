---
title: "Mounting VFAT after 10.04 upgrade"
date: 2010-05-13
forum: Mythbuntu
---

### Post by Boppy3125 on 2010-05-13
This thread [[http://ubuntuforums.org/showthread.php?t=1472280]](http://ubuntuforums.org/showthread.php?t=1472280]) has some similar problems but mine is local HD with a VFAT partition that had mounted just fine prior to upgrading.  I eventually got to a desktop tonight, but when I try to mount this partition I get an error.

```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error

```
checking dmesg I see:
```
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev sdb1.

```

I find it surprising that this partition would crap out during a dist upgrade.  What kind of troubleshooting steps can I try.  Maybe it is something in my fstab.  I have recording that my database thinks are here, so if I have to I will get into removing those, but I would prefer to keep it as is if I can.  Should I try a live CD?  (I don't think I have one handy but I could download Mythbuntu 10.04.)

---

### Post by Boppy3125 on 2010-05-14
Sorry, don't know what happened but it was the assignment of the two drives getting swapped.  sdb<==>sda

I sorted it all out and changed these two to use UUID and it looks like I am back in business.

---

