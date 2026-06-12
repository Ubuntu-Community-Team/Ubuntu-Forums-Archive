---
title: "Mounting already smbfs mounted folders via sshfs"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by kartal on 2009-11-29
Hi

Here is my case

I have a windows pc that I can mount-access via smbfs no problem. All the mounted folders(from Windows) reside under /mnt. I can access them, delete them write them etc no problem. 

I use sshfs from another laptop to connect-mount to the linux computer(the one that has windows mounts). I normally have no problem mounting write access linux folders with this laptop and the Ubuntu one. 

My problem is that when I mount the folders that are in the Ubuntu`s /mnt folder(which are windows shares) via Sshfs on my other laptop(Xubuntu) I can only get read access, I have no write access at all. I tried changing the group rights access of those folders in /mnt but did not help at all. All the users are in samba users as well, and the user that is trying to access the mounted folders via Sshfs is a legitimate user on the Windows box that serves the shares.


I would appreciate any help or insight


thanks

---

### Post by kartal on 2009-11-29
Btw here is how one of my fstab line looks (The Ubuntu laptop with /mnt/windows shares)

//192.168.2.106/q	/mnt/q	smbfs	credentials=/home/user/.credentials,uid=user,gid=users,umask=0000	0	0

Basically when I mount this drive I see that the owner has full access but the users have only read access. Maybe that is the issue. But I cannot find a way to change that.

---

### Post by brunojcm on 2012-06-03
Are you using the owner of the smbfs shares to make the sshfs shares on the other machine? I think this is the problem.

---

### Post by Iowan on 2012-06-03
Thread has been inactive fro 2.5 years.

---

