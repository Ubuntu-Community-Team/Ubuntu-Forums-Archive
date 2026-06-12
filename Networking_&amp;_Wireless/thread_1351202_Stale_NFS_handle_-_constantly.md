---
title: "Stale NFS handle - constantly"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by itzfritz on 2009-12-10
I have a Fedora 11 box serving as a file server, and mount NFS shares on my Jaunty box (as well as other machines).
I am however constantly getting "Stale NFS Handle" errors scattered throughout these mount points - for example, 17 out of 20 directories in a mounted share might become stale, while the others work fine.  This happens intermittently.

There are no errors on either box.  The only fix is a `umount /mnt/nfs && mount -a` on the jaunty box.  The Fedora box serves several NFS clients, Jaunty is the only problem.

The NFS share on the Fedora box is odd, in that it is an NTFS partition sitting on an NVIDIA dmraid array in /mnt; but, since no other box has any problems, i suspect this is unrelated.

HELP!  I don't want to use Samba for linux<->linux file sharing :(

---

