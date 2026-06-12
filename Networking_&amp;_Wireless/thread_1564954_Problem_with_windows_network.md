---
title: "Problem with windows network"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by Hcore8 on 2010-08-31
Hi everyone,
I made up a LAN between both my computers the laptop running WINDOWS XP and the desktop running Ubuntu 10.04.
I used to be able to go to places>network>windows network and I could see all my shared files on ubuntu but I recently messed up with my ubuntu and now I can't access the windows network from ubuntu anymore it gives me an error like this:
- Unable to mount location
  Failed to execute child process "/usr/lib/gvfs/gvfsd-smb-browse" (No such file or   directory)
I don't know how to fix the problem. Does anyone have a clue to this? please help me!

---

### Post by MaindotC on 2010-08-31
We need a little more information about when you said "I recently messed up with my ubuntu".  What exactly happened?

---

### Post by endotherm on 2010-08-31
what is the output of 
```
ls -al /usr/lib/gvfs
ls -al ~ | grep .gvfs

```

what happens if you launch nautilus as admin (Alt + F2, and enter 'gksu nautilus') then try to access the share. does it work then?

---

### Post by dipspesh on 2011-04-28
I'm facing the same problem,BUT i have just installed samba on my pc!
and the output of the above commands is 

deepesh@Truthseeker:/etc/init.d$ ls -al /usr/lib/gvfs
total 768
drwxr-xr-x   2 root root   4096 2011-04-28 15:04 .
drwxr-xr-x 242 root root  73728 2011-04-28 15:41 ..
-rwxr-xr-x   1 root root 121504 2010-05-12 15:28 gvfsd
-rwxr-xr-x   1 root root 129928 2010-05-12 15:28 gvfsd-computer
-rwxr-xr-x   1 root root 133788 2010-05-12 15:28 gvfsd-localtest
-rwxr-xr-x   1 root root  51184 2010-05-12 15:28 gvfsd-metadata
-rwxr-xr-x   1 root root 133948 2010-05-12 15:28 gvfsd-trash
-rwxr-xr-x   1 root root  26656 2010-05-12 15:28 gvfs-fuse-daemon
-rwxr-xr-x   1 root root  96864 2010-05-12 15:28 gvfs-gdu-volume-monitor
deepesh@Truthseeker:/etc/init.d$ ls -al ~ | grep .gvfs
dr-x------  2 deepesh deepesh         0 2011-04-28 14:25 .gvfs

any help regarding this would be highly appreciated!

---

### Post by dipspesh on 2011-04-28
Problem is solved!! :D

I just installed the package **gvfs-backends **and now i'm able to browse the contents on the network!
The file gvfs-smb got installed by installing that package!! :)

---

