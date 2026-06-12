---
title: "NFS mount produced circular links on Urix"
date: 2011-06-20
forum: Networking &amp; Wireless
---

### Post by steveborland on 2011-06-20
I was setting up an Ubuntu server for a client who runs a rather old version of Irix on an SGI O2 machine (he uses some design software that does not run on newer hardware).

This version of Irix can only use NFS V2 or V3, so I setup the exports file on Ubuntu to use nfs3. However, when the file system was mounted on Irix, everything (including flat text files) was mounted as a directory, i.e. everything in the Ubuntu directory was mounted as a circular link to its' self

After _much_ faffing about, I found that using nfs2 in the exports file fixed the problem, and the client was a happy camper again.

Does anybody have an explanation for this? I've never seen this problem before, nor have I found any reference to it on the net.

I cannot be the only person in the world who needs to connect to old Unix systems?

/Steve.

---

### Post by Zsolt Hidasi on 2011-07-21
Dear Steve,

I have the same problem as your client. I have an old O2 machine and sometimes I use it. Not so long time ago I had another old PC with a Mandrake Linux 9.2 and was able to connect the O2 via NFS mount without any problem. Now I had to put the old Mandrake machine away so I should connect to the O2 from my Ubuntu machine but I can't :-(

It seems to me, that the mounting is OK (at least there is not any message concerning to an unsuccessful mount), but after the mounting I cannot change the directory to the mount point (the command prompt just waits). I've tried to mount my Ubuntu from the O2, too, almost with the same result. It's very strange because I can change the directory to the mount point, moreover to its subdirectories, but cannot see anything (if I type eg. ls than nothing happens). My exports files are very simple on both of the systems, because there is not any important restrictions as I am the only user who uses it and the two machines wired only temporarily.

I've read your in your message that "using nfs2 in the exports file fixed the problem" but I don't know how can I indicate in the exports file, that it's an nfs2 version. Off course I've "googled" this subject and passed days to solve my problem without any success. Would you so kind to details the solution?

Thanks a lot: Zsolt

PS.: sorry for my poor English

---

