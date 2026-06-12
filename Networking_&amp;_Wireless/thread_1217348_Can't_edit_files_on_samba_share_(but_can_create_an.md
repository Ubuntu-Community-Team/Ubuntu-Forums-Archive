---
title: "Can't edit files on samba share (but can create and delete). And it works in Windows."
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by bernied on 2009-07-19
I can no longer edit files on a samba share, which I used to be able to do.

Does anyone know if something has changed in the last six months or so that would affect this?

On the server (it's a Linksys NSLU2 - aka slug - NAS device running Debian ARM):
```
slugger: ~ # uname -ar
Linux slugger 2.6.18-4-ixp4xx #1 Sun Apr 22 08:34:11 UTC 2007 armv5tel GNU/Linux
slugger: ~ # cat /etc/samba/smb.conf

[global]
workgroup = MURIESTON
netbios name = slugger
server string = Music server
hosts allow = 192.168.0. 192.168.1. 127. 10.5.11.
log file = /var/log/samba/log.%m
max log size = 50
log level = 4

guest account = guest
security = share

socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

preserve case = yes
short preserve case = yes
default case = lower

[share]
   comment = File Store
   path = /mnt/store/share
   read only = no
   writable = yes
   public = yes
   only guest = yes
   create mask = 0660
   directory mask = 2770
   force directory mode = 2770

--- snipped ---

slugger: /mnt/store/share/Music/temp # ls -al
total 24
drwxrws---  2 guest guest  4096 2009-07-19 18:59 .
drwxrwsr-x 14 guest guest 20480 2009-07-19 18:58 ..
-rw-rw----  1 guest guest     0 2009-07-19 18:59 test
```
On the client (Ubuntu Jaunty):
```
bernie@ubuntu:~$ uname -ar
Linux ubuntu 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64 GNU/Linux

bernie@ubuntu:~$ cat /etc/fstab | grep slugger
//192.168.0.98/share /media/slugger cifs user=guest,passwd=,rw,auto,_netdev 0 0
bernie@ubuntu:~$ mount | grep slugger
//192.168.0.98/share on /media/slugger type cifs (rw,_netdev,user=guest,passwd=)

bernie@ubuntu:~$ cd /media/slugger/Music/temp/
bernie@ubuntu:/media/slugger/Music/temp$ ls -al
total 0
drwxrws---  2 share share 0 2009-07-19 18:59 .
drwxrwsr-x 14 share share 0 2009-07-19 18:58 ..
-rw-rw----  1 share share 0 2009-07-19 18:59 test

bernie@ubuntu:/media/slugger/Music/temp$ groups
bernie adm dialout cdrom plugdev lpadmin admin sambashare mythtv share

bernie@ubuntu:/media/slugger/Music/temp$ touch test2
touch: setting times of `test2': Invalid argument
bernie@ubuntu:/media/slugger/Music/temp$ ls -al
total 0
drwxrws---  2 share share 0 2009-07-19 19:02 .
drwxrwsr-x 14 share share 0 2009-07-19 18:58 ..
-rw-rw----  1 share share 0 2009-07-19 18:59 test
-rw-rw----  1 share share 0 2009-07-19 19:02 test2

bernie@ubuntu:/media/slugger/Music/temp$ echo 'blah' >> test2
bernie@ubuntu:/media/slugger/Music/temp$ cat test2
blah

bernie@ubuntu:/media/slugger/Music/temp$ rm test
bernie@ubuntu:/media/slugger/Music/temp$ ls -al
total 4
drwxrws---  2 share share 0 2009-07-19 19:19 .
drwxrwsr-x 14 share share 0 2009-07-19 18:58 ..
-rw-rw----  1 share share 5 2009-07-19 19:04 test2

bernie@ubuntu:/media/slugger/Music/temp$ nano test2
```
But here's where it all goes wrong, because nano tells me:
```
 [ Error writing test2: No such file or directory ]
```
I don't care so much about nano, my biggest issue is updating tags using EasyTag, which gives this message:
```
Can't write tag in file 'Song.mp3'! (Operation not permitted)
```
Does anyone have any ideas?

I don't have any problems editing the same files using a Windows client. (But I can't try either nano or EasyTag)

Thanks
Bernie

---

### Post by bernied on 2009-07-26
Is there anyone who can please post a samba share definition and the corresponding entry in fstab that works for them? I'm looking for a share that can be accessed by anyone, for both reading and writing, with no authentication, in both Windows and linux environments. This should not be complicated.

Thanks
Bernie

---

### Post by EnlistedSquire on 2009-10-22
I'm having the same problem.

Previously I'd no trouble with Samba shares hosted on a Windows server but that machine died so I've replaced it with a Linux server.

I can access the shared directory via Windows Explorer and via the Ubuntu (9.04) "Connect to Server" option with no problems.

However, as soon as I try to mount the share on the same Ubuntu box via fstab things go wrong. This way I can browse, open, delete and create files, but I can't edit existing files. I don't get permission errors, it's more as if the share is totally inaccessible to the application I'm using.

This is my line in fstab as it is at the moment:

```
//192.168.10.1/storage /mnt/darren/storage smbfs credentials=/root/.credentialsdarren,gid=users 0 0
```

I've also tried any number of different options on that line such as mask, gid, uid, user etc. etc. but everything's giving the same result.

Can someone post their line from fstab as there must be an option I need to set that I haven't tried so far?

Thanks.

---

### Post by EnlistedSquire on 2009-10-22
As usual a night of searching the interwebs turns up nothing and the minute I post a question in a forum I find the answer. :roll:

The option "nodfs" works for me but others have also reported success with "nounix".

---

