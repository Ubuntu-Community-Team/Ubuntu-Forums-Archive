---
title: "fusesmb OK in one user but some permissions denied in other user"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by Redsandro on 2009-07-27
Hi, 

I've got a Xubuntu 8.10 media center here using XBMC.
**xbmc** is a non-admin autologin user that fuses samba on a network folder on the desktop. Everything works.

When I log out and log in as **sander**, which is my personal admin user, a same fusesmb action is performed on that Desktop/network folder.

However, my Windows 7 machine won't show up until I fusesmb.cache. But even then, all the shared folders from that machine get **Permission Denied**. All other computers and their folders show up just fine, without permission problems.

How come? I don't get it.

When running **mount**, you can see both the mounts active:
```
fusesmb on /home/xbmc/Desktop/network type fuse.fusesmb(rw,nosuid,nodev,max_read=32768,user=xbmc)
fusesmb on /home/sander/Desktop/network type fuse.fusesmb(rw,nosuid,nodev,max_read=32768,user=sander)
```

I tried to **umount** the first one in case there's some login count restriction, but even after waiting a long time [SIZE="1"](iirc Windows sessions are closed after 10 minutes on the Windows end)[/SIZE] and .cache'ing, the shares from that machine are still inaccessible.

Any ideas?

---

### Post by Redsandro on 2009-07-27
There was something about the permissions of the folder being root but it's never been a problem and fixing it does not fix the problem.

But just so you know, I changed it like so:
```
\home\xmbc\Desktop
drwxrwxr-x  2 xbmc fuse 4.0K 2009-02-22 08:51 network

\home\sander\Desktop
drwxr-xr-x  3 root   root   4.0K 2009-07-27 15:14 network

$ sudo umount /home/sander/Desktop/network/
$ sudo chown sander:fuse ./network/
$ sudo chmod g+w ./network/
$ ls -lah
drwxrwxr-x  2 sander fuse   4.0K 2009-02-22 07:55 network
```
Still the same problem though :(

---

