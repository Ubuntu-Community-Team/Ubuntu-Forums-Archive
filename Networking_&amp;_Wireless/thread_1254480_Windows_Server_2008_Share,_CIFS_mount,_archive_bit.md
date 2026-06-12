---
title: "Windows Server 2008 Share, CIFS mount, archive bit"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by skolem on 2009-08-31
Hi,

I have the following issue:

I'm running Ubuntu 8.04 and Samba 3.0.28. I'm trying to mount a Windows share that lives on a Windows Server 2008 via

mount -t cifs //xx.yy.zz.uu/share /mnt/share

which works. But now I need to check, if the archive bit of a specific file is set or not. When I try 

getfattr -d /mnt/share/file

it gives me nothing. Even when I try mount options like user_att or acl I get the same result. I have the CIFS extended attribute support compiled into the kernel, so I'm able to set extended attributes like

setfattr -n user.someattr -v blub /mnt/share/file

and then get it back

getfattr -d /mnt/share/file
getfattr: Removing leading '/' from absolute path names
# file: mnt/share/file
user.SOMEATTR="blub"

But i'm not able to get the Windows archive bit. Is there a way to achieve this?

Thanks a lot
Sven

---

