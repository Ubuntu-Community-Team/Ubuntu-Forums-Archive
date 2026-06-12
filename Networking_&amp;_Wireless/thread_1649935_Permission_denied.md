---
title: "Permission denied???"
date: 2010-12-20
forum: Networking &amp; Wireless
---

### Post by glennzo on 2010-12-20
Hello all. I've mounted an NFS share from a Fedora box to a folder on an Ubuntu 10 box. Now I get errors trying to list the contents of the folder. Funny, I was able to mount it no problem.

The mount command:
> [glenn@ubuntu10 ~>$ sudo mount -t nfs4 donatello:/home/glenn/ /mnt/folding/donatello/
No error. Mounted just fine.

Try to list the contents of said mounted folder and it seems a different story.

> [glenn@ubuntu10 ~>$ ls -la /mnt/folding/donatello/
ls: cannot open directory /mnt/folding/donatello/: Permission denied

[glenn@ubuntu10 ~>$ sudo ls -la /mnt/folding/donatello/
Password: 
ls: cannot open directory /mnt/folding/donatello/: Permission denied

I'm confused. Looks like I wouldn't even be able to umount the share. Any  thoughts?

---

