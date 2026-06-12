---
title: "nfs automount"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by siegi on 2009-04-05
I want to automount a nfs share on my server. 
But the server is not always running. I used autofs with the timeout to umount the partition on time. This works fine, but when the server is not running, and a program tries to access a file on the nfs mount, the program freezes. I would be better to just have an error that the file is not there.
Are there any idea's to fix this? 
Thanks in advance.

---

### Post by renkinjutsu on 2009-05-02
bump.. i have this problem too
and nautilus freezes when i try to umount when the server is shutdown.

another NFS question.. is it possible to mount another NFS share onto folder N2 and have that folder under N1 which is also shared through NFS
if desktop2 mounts N1 .. will they have access to the NFS share mounted onto N2?

---

### Post by lensman3 on 2009-05-02
Use the "soft" option to mount the directory on the local machine.  Nfs has always shown this behavior when the server is not online.  By definition, a server is always running.  You also might have to add the option "timeout=n" where n is in 10ths of seconds.  The default timeout is 60  seconds. 

Do a "man nfs" for the options. The man page is for /etc/fstab but it is also true for autofs.

---

### Post by ugm6hr on 2009-05-13
I have set up autofs for my FreeNAS NFS share as below:

Install autofs first:
```
sudo apt-get install autofs
```

/etc/auto.master
```
/home/*username*/Network         /etc/auto.freenas  --timeout=60
```

/etc/auto.freenas
```
*freenas1*  -fstype=nfs	*192.168.1.250:/mnt/freenas1*
```

Where *username* is my username (i.e. it mounts in my home folder), *192.168.1.250:/mnt/freenas1* is the network mount point for the NFS share, *freenas1* is the local folder to mount the network drive (should not already exist).

As for mounting NFS folders within each other, I don't think that's possible, since autofs looks for the mountpoint at login.  However, 2 separate entries can be made, so N1 and N2 can be mounted within the same directory.

autofs should unmount after a set timeout.  If accessing files with an offline server is a problem, consider reducing the timeout period to ensure that the share is unmounted if not accessed.  According to the greenfly link below, the timeout is in seconds.

Refs: [http://www.greenfly.org/tips/autofs.html](http://www.greenfly.org/tips/autofs.html) [https://help.ubuntu.com/community/SettingUpNFSHowTo#Mounts](https://help.ubuntu.com/community/SettingUpNFSHowTo#Mounts)

---

### Post by siegi on 2009-05-24
Thanks for your replies 
@lensman3 soft mount doesn't fix the problem.

@ugm6hr, My configuration is simular. 
By example 
When the server is not running/available and the nfs share is not mounted. And dolphin tries to access the nfs share, dolphin hangs. 

The problem is located in nfs-common. It's taking to long to timeout the mount request.
[https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/234480](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/234480)
I've installed the gutsy version.

---

### Post by ugm6hr on 2009-05-24
> **siegi said:**
> When the server is not running/available and the nfs share is not mounted. And dolphin tries to access the nfs share, dolphin hangs. 

Actually, I have realised this is the case too.

I tried to mount my NFS shares when I was travelling (i.e. away from my LAN with the server), and nautilus appears to hang indefinitely.

Shame, SMB doesn't appear to suffer the same problem.

---

### Post by mal on 2009-05-24
There is a bug in nfs-common that causes this autofs behaviour.  See [https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/234480]("https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/234480").

There does not seem to be much action on this, so I guess it is not seen as important enough for developer attention.

I have given up on autofs for this reason.

Mal

---

### Post by siegi on 2009-08-04
I still have the problem. Is there anyone with another tip, I'm think, I can better remove autofs.

---

### Post by ugm6hr on 2009-08-12
Try using Xfce / thunar.

Thunar tries to look for the share, but doesn't freeze the entire desktop (unlike Gnome / nautilus).  After a while (perhaps 40-60 secs), it just gives up.

Uncertain what would happen if another application was to access it directly.

---

