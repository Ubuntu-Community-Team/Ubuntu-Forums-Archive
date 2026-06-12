---
title: "simple explanation of fuse/sshfs permissions"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by Knacker on 2011-05-15
I'm trying to get the software for a newly purchased squeezebox to find my music which is stored on a NAS and mounted on my Ubuntu Desktop using SSHFS. It can't find it and I think the reason has to do with permissions. The SSHFS is mounted at /media/fork and here is what I get from ls -l 

drwxr-xr-x 1   1024 users  4096 2011-05-15 21:09 fork


I set up the SSHFS so long ago that I don't remember how I did it. I'm still pretty much a beginner here, so I don't really know where to begin. Is there a simple way for me to change the way that the owner and permissions for SSHFS mounted folders work when I mount them? I stress simple...I really don't want to screw anything up. 

Thanks in advance!

EDIT: Weird: when I checked permissions for subfolders, they were surprisingly different. Does this mean that the problem is on the server/daemon side? Here's the output for ls -l within the /media/fork/  :

drwxr-xr-x 1 1024 users 4096 2011-05-15 15:57 Folder1
drwxrwxrwx 1 1024 users 4096 2011-05-15 15:57 Folder2
drwxrwxrwx 1 1024 users 4096 2011-05-15 21:09 Folder3
drwxrwxrwx 1 1024 users 4096 2010-05-23 17:55 Folder4
drwxr-xr-x 1 1024 users 4096 2010-04-09 05:08 Folder5
drwxrwxrwx 1 1024 users 4096 2011-05-11 04:12 Folder6

---

