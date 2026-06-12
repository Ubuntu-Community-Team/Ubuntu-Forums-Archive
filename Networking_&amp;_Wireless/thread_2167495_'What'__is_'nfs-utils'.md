---
title: "'What'  is 'nfs-utils'???"
date: 2013-08-13
forum: Networking &amp; Wireless
---

### Post by omelette on 2013-08-13
As per the title, what exactly is the package 'nfs-utils'?

Launchpad list it [here]("https://launchpad.net/ubuntu/+source/nfs-utils") as **"nfs-utils provides the required support programs for using the Linux kernel's NFS support, either as a client or as a server (or as both)."**  Whereas [this]("http://packages.debian.org/source/wheezy/nfs-utils") site says;

> The following binary packages are built from this source package:

nfs-common
    NFS support files common to client and server
nfs-kernel-server
    support for NFS kernel server 

But this does not seem to be the case.  I have built & installed 'nfs-utils' and 'nfs-kernel-server' is nowhere to be found.  Moreover, there is a package-conflict if you then try to install 'nfs-kernel-server' - or more precisely, a conflict between 'nfs-utils' and 'nfs-common', which 'nfs-kernel-server' lists as a dependency.

Why I hear someone ask not just install 'nfs-common' and 'nfs-kernel-server' and be done with it?  Well, first 'nfs-utils' seems a much newer package - version 1.2.8 versus 1.1.2 - and second, there seems to be a nasty bug which is easily reproducible in 'nfs-common'.  One of my computers (my 'NFS client' in this instance) I leave running 24/7, my server is switched off at the end of the day.  It happens without fail that when I restart my server and my client computer detects & mounts it, (with the help of '[nfs_automount]("https://github.com/vwal/nfs_automount")') the NFS-client software will either lock up immediately, or else shortly after when a file-transfer is in progress.  This results in Nautilus locking up, the only solution then being to reboot!

Whereas when I built and installed 'nfs-utils', this no longer happened.  In other words, if you install 'nfs-utils', you have a working nfs-client, but haven't, and **cannot have**, a working server on the same machine due to the package-conflict.  But I would also like the nfs-server running on the 'client' pc, hence this thread.

---

### Post by omelette on 2013-08-28
Bump!

If anyone has some info on 'nfs-utils' it would be appreciated.  I have installed it on 2 computers, one of which has **'nfs_automount'** running, so will auto-mount any detected nfs shares.  I was surprised to see that it does actually detect a mounted-share from the other computer, and disheartened to see that nfs_automount keeps mounting/unmounting the share.  When it is mounted, I succeed in transferring a small file in either direction, but it's excruciatingly slow - probably akin to a 300 baud modem!

But at least it confirms that there is a nfs-server included in nfs-utils, even if it isn't working properly.  Apart from installing nfs-utils on both machines, the only other thing that I have done is edit the /etc/exports file as instructed with the old nfs-common/nfs-server setup.

Edit:  Just to add, with nfs-utils installed on one machine and nfs-common/nfs-server installed on the other, nfs_automount works perfectly, mounting the detected-share just once - ie. the problem is with nfs-utils, not nfs_automount.

---

