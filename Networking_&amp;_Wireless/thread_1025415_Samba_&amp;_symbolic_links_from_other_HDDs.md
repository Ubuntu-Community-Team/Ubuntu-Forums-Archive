---
title: "Samba &amp; symbolic links from other HDDs"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by trumpeteersman on 2008-12-30
I made a symbolic-linked directory tree in a Samba share folder called "Public".  These links come from all over the place: From my home folder, from a home folder on an fstab-mounted Debian Etch HDD, and from a home folder from a fstab-mounted Ubuntu Dapper HDD.

Permissions of share folder
drwxr-xr-x  6 mainuser sharer  4096 2008-12-29 22:48 Public

There is a user and group named "sharer" in which networked users have to login as in order to access the share folder "Public".

I can login from both Windows XP and from another Ubuntu Hardy and access this directory.  However, only the symlinks from the hosts HDD and the Debian HDD are shown.  The symlinks from the Dapper HDD are missing.

I checked the permissions of the Dapper HDD and they are 775 recursively.  And the owner of the original files is the same user as the Host HDD.

I tried what this guy did, but to no avail:
[http://ubuntuforums.org/showthread.php?t=901821](http://ubuntuforums.org/showthread.php?t=901821)

This is my smb.conf:
```


[global]

follow symlinks = yes
wide symlinks = yes
unix extensions = no
workgroup = WORKGROUP
; wins support = no
; dns proxy = no
encrypt passwords = true
obey pam restrictions = no
invalid users = nobody

[PUBLIC]
path = /home/txzor/Public/
valid users = sharer
guest ok = no


```

I changed the "obey pam restrictions = yes" to no, but that did not change anything.

Here is my fstab:

```

#UbuntuRoot (hda3 for Debian)
/dev/sda3       /media/ubunturoot       ext3    relatime,errors=remount-ro      0       0

#DebianHome (hdc5 for Debian)
/dev/sdc5       /media/debianhome       ext3    relatime,errors=remount-ro      0       0


```



Any ideas as to what the problem could be?

---

