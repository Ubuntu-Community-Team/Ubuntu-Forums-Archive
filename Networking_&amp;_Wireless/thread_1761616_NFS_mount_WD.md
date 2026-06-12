---
title: "NFS mount WD"
date: 2011-05-18
forum: Networking &amp; Wireless
---

### Post by krumpy on 2011-05-18
I'm running into permissions issues whenever I try to make changes on the mounted network drive.  So for example I can't do something like sudo chown (however I can create a file, copy files, etc).  

The main problem is I want to use rsync for backup, but I get tons of permission denied error msgs every time I run it.  Can anyone help me out here?  I'm assuming that It's the etc/exports entries but after many hours of googling I haven't been able to fix it.  One other thing I am able to ssh into the drive as root and have full permissions.    

Here is my fstab entry:
MyBookWorld:/DataVolume/Public  /media/netdrive                      nfs     rw              0       0 

and my etc/exports entry on the external HD
/nfs/Public *(rw,all_squash,sync,insecure,anonuid=65534,anongid=1000)
/nfs/Download *(rw,all_squash,sync,insecure,anonuid=65534,anongid=1000)
/nfs/matt *(rw,all_squash,sync,insecure,anonuid=65534,anongid=1000)

---

### Post by krumpy on 2011-05-18
I think I figured out a solution.  Just remove all_squash and replace with no_root_squash in the /etc/exports file.  

The guide on source forge says that there are serious security implications of this (
[http://nfs.sourceforge.net/nfs-howto/ar01s03.html](http://nfs.sourceforge.net/nfs-howto/ar01s03.html)), however this drive that I am mounting is only my network backup drive therefore I don't see the problem (I'm the only user on the network).  If I understand correctly someone running a large network wouldn't want to do this as local root access effectively gives the user root permissions on the network drive as well.  Any feedback would be greatly appreciated as I'm still very new to Linux.

Here is what I was going to use as my /etc/exports file:

new:
nfs/Public 192.XXX(rw,no_root_squash,sync)                                                                                            
/nfs/Public 192.XXX(rw,no_root_squash,sync) 

original:
/nfs/Public *(rw,all_squash,sync,insecure,anonuid=65534,anongid=1000)

---

