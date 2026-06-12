---
title: "Can't see Windows share folders"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by mws604 on 2009-04-13
I have three PCs running XP, one PC running Vista, and one PC running Ubuntu 8.04.   The Windows PCs can all read, write, and delete files on the MyFiles Samba share but the Ubuntu PC detects the MSHOME workgroup but cannot see any of the share folders on the Windows PCs.

The only posts I have seen dealt with problems configuring samba.  Has someone else had this problem and if so, have they identified a solution?

---

### Post by mws604 on 2009-04-14
What I have further discovered ...

Part of the problem is that ubuntu is not able to resolve the Window PC hostnames to IP addresses (at least when I ping the hostnames on the ubuntu box), they don't resolve whereas on the Windows boxes they do.

Also, if I type the ip address (smb://192.168.1.1XX) for one of the Windows PCs in nautilus,  I can see the share folders just fine.

---

### Post by inobe on 2009-04-14
check out this thread [http://ubuntuforums.org/showthread.php?p=7062296#post7062296](http://ubuntuforums.org/showthread.php?p=7062296#post7062296)

have you followed the ubuntu documentation' especially **"Sharing folders via the Shared Folders application"** part ?

[https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html) steps 1 to 11.


sounds like you have shares via nautilus !

---

### Post by dmizer on 2009-04-14
> **mws604 said:**
> What I have further discovered ...

Part of the problem is that ubuntu is not able to resolve the Window PC hostnames to IP addresses (at least when I ping the hostnames on the ubuntu box), they don't resolve whereas on the Windows boxes they do.

Also, if I type the ip address (smb://192.168.1.1XX) for one of the Windows PCs in nautilus,  I can see the share folders just fine.

To configure your Ubuntu computer for browsing netbios names (Windows hostname), follow this: [http://ubuntuforums.org/showthread.php?p=7069067#post7069067](http://ubuntuforums.org/showthread.php?p=7069067#post7069067)

---

