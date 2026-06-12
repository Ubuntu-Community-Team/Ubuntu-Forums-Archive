---
title: "Sharing a partition mounted to a folder"
date: 2010-04-07
forum: Networking &amp; Wireless
---

### Post by qwert231 on 2010-04-07
I have a drive on my system that mounts to /storage/ .

I would like to share the whole thing to Windows users with write enabled. I can see and browse the share from a Windows box, but cannot create files on it. This is the only share I've set up on the linux server, and since no OS files are under the share, I'm not too worried about it.

I'm using Ubunto 9.10.

Things I've tried:
Sharing it w/ Samba... done. I can see the drive from my Windows box. (Windows user is 'Us' and the user/pass match the linux 'Us' user.)

sudo chgrp -R users /storage ... doesn't happen. The group stays as root.

mark@fileServer:~$ grep samba cat /etc/group
grep: cat: No such file or directory
/etc/group:sambashare:x:122:mark,Us

mark@fileServer:/$ ls -l
total 100
...
drwxrwxrwx   1 root root  8192 2010-03-28 20:54 storage


mark@fileServer:/$ cat /etc/samba/smb.conf
[storage]
comment = Storage folder
read only = no
path = /storage
browseable = yes


mark@fileServer:/etc/samba$ cat /etc/fstab
...
UUID=7F960C9B315CC624   /storage        ntfs    rw,user,auto


What am I missing?

---

### Post by qwert231 on 2010-04-07
Restarting Samba after adding 'Us' to the sambashare group seemed to get me in.


However, this was working previously.

Then again, when I was writing to the share earlier, I was using:
\\192.168.xxx.yyy\storage\folder\

And this time I was trying:
\\Fileserver\storage\folder\

---

