---
title: "mount error(13): Permission denied"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by Hammi on 2009-12-26
When googling around, I've seen quite a few posts related to this message, but none has really helped me further, so I'm posting my question here:

I have 3 Ubuntu machines, one 8.04.3 LTS server (192.168.1.55) and two 9.10 clients (192.168.1.5 and 192.168.2.29). I have a samba share on the server, which I can access from Windows clients as well as from one of the two 9.10 clients using this command:

```
mount -o guest //192.168.1.55/netstore /mnt/server
```When I run the same command on the other 9.10 client, I get:

```
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```as well as

```
Dec 26 21:27:34 server1 kernel: [558169.547446]  CIFS VFS: cifs_mount failed w/return code = -13
```in the syslog.

smbfs is installed on both 9.10 clients. 

netstore is configured on the server as follows:

```
[netstore]
   comment = network storage drive
   path = /srv/netstore
   guest ok = yes
   writeable = yes
   writable = yes
   available = yes
   browseable = yes
   hosts allow = 192.168.
   read only = no
   force create mode = 0777
   force directory mode = 0777

```/srv/netstore on the server is set to 777. 

I've followed the how-to there: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534) but with no success...

I would really love to know what the issue might be: It can't be a username issue, if I'm trying to access as guest, right? But the path permissions for the mount point are set identical on both 9.10 clients...

I'm lost. Thanks for any helpful hints.

---

### Post by ubori on 2010-01-05
Try adding the following options (after -o) to your mount in /etc/fstab (or your mount command).
dir_mode=0777,file_mode=0777,gid=users,rw

---

