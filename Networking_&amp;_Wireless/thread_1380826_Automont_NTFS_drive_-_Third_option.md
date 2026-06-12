---
title: "Automont NTFS drive - Third option"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by ^_Pepe_^ on 2010-01-14
Hi all.

I have a laptop, with 9.10, Wifi connected. I want it to connect at startup for all users (my wife, my son and me) to a NTFS-formatted hard disk, located on a server, with 9.10, ethernet connected, always on. 

1st option. I've tried CIFS. Well, it's the common option, and works well. Following this incredible post (thanks again) [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534) it worked. But...I've found this bug, [https://bugs.launchpad.net/bugs/211631](https://bugs.launchpad.net/bugs/211631), that cannot be solved easily in Karmic. (9.04 can be workarounded changing some scripts). 

2nd option. NFS. Let's go. Easy to setup. But...bug again. As the unit is NTFS formatted (I've tried ext4 with success), this is bug [https://bugs.launchpad.net/ubuntu/+bug/499756](https://bugs.launchpad.net/ubuntu/+bug/499756). NFS client shows "Stale NFS file handle". No way. Only unmount and remount works.  I've found some information about autofs could work, but no updated information found. Is it deprecated?

3rd option. SSH. Let's go. I've learnt to SSH my server passwordless. This is ok, for my client-side user (me) and root. Bug, if I include mount option in /etc/fstab, it's mounted! and root can access the mounted file. But my user can't. 

Please, can anybody help me with autofs option or SSH final "push"??

Does nobody any similar case? I think it should be quite common, mainly because my NTFS unit needs to be so, because is also shared with a Windows-based machine (HTPC).

Thanks in advance
^_Pepe_^

---

