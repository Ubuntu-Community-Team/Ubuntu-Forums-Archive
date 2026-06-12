---
title: "Shared folders"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by makaveli0129 on 2009-01-07
i have 2 computers 1 laptop and 1 desktop on the desktop i have a shared folder (ntfs) that i can access from either linux or windows on my laptop. The problem is that this only works if the desktop is in windows. I need to know when i have the desktop in Ubuntu how do i access the ntfs folder from linux on my laptop.
Essentially 1 shared ntfs folder in linux and access it from another linux computer? Would samba work for this or no?

---

### Post by 2hot6ft2 on 2009-01-07
Might take a look at these.
[http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

and
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

I don't know anything about samba, but I'm sure it can be done.

---

### Post by Iowan on 2009-01-07
The NFS How-To may not help with the NTFS share.  Seems like there's information around here to let Ubuntu use NTFS.  Samba *might* work.  You *might* be able to mount the NTFS share via [fstab]("http://ubuntuforums.org/showthread.php?&t=283131").

---

