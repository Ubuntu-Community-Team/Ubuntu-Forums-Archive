---
title: "Mount NAS using NFS"
date: 2011-04-25
forum: Networking &amp; Wireless
---

### Post by Bobbycreekwater on 2011-04-25
I have a WD ShareSpace in which I am trying to mount on my Ubuntu desktop.  I've spent a few hours on this and all seems well up until the point where I run the following code - 

~$ sudo mount -t nfs -o proto=tcp,port=2049 192.168.1.50:/NFS/Public WDSS

and get the following error:

mount.nfs: access denied by server while mounting 192.168.1.50:/NFS/Public


I'm so filled with frustration right now and I would appreciate any help.  I'm new to Ubuntu (3 days) and the only thing I could provide is that the WD Share Space manual tells me that the mount point for the NFS is "/nfs/Public"

Does it matter that the NAS is password protected? (i.e. when I log onto under Windows 7 it requires a user/pass).  

I would love to use Ubuntu as my main OS but the NAS is where all my files are maintained.  

Thanks in advance!!!

---

