---
title: "NFS mount becomes unresponsive??"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by ThomWilhelm on 2010-04-27
I am currently trying to share 2 subdirectories from one Ubuntu PC (which are very spaced out within the filesystem) with another Ubuntu machine, I would like to just export them as one directory for simplicity.

I am creating these 2 directories as subdirectories of a single directory on the server machine with the fstab file:

/var/dir1       /share/dirname/dir1 none    bind    0       0
/var/dir2       /share/dirname/dir2 none    bind    0       0

Where /var/dir1 and /var/dir2 represent the directories I wish to share and /share/dirname is the directory I plan to share to other computers, so I have used fstab to bind these directories inside the /share/dirname directory.

My /etc/exports file on the server looks like:

/share/dirname  169.254.*(ro,async,nohide,fsid=0,no_root_squash)
/share/dirname/dir1 169.254.*(ro,async,nohide,no_root_squash)
/share/dirname/dir2 169.254.*(ro,async,nohide,no_root_squash)

Then from the client machine, I have added this to the fstab:

169.254.213.150:/share/dirname      /mount/dirname      nfs     rsize=8192,wsize=8192,timeo=14,intr

Here is the strange behaviour. This WORKS when I reboot the client machine and I can access both subdirectories just fine, but it seems to disconnect and the mounted files are not accessible after around 20 minutes!

Any ideas? Are there any logs file that can tell me why?

Just for reference, the directories I am mounting from the server are quite large, around 4GB each.

Thanks,
Thom.

---

### Post by ThomWilhelm on 2010-04-28
Any ideas anyone?

---

### Post by Taliwn on 2011-11-29
We currently face the same problem, could you find any solution to this?

---

