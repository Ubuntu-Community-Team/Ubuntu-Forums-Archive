---
title: "Problem with Samba share permissions"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by cian1500ww on 2011-04-24
I'm having some trouble mounting a Samba share on my two Ubuntu machines. The Samba share is setup so that all files are readable and writable by everyone (it's only accessible via the local network). When I create a new folder on the share with either of my Ubuntu machines, the folder becomes non-writable by anyone ie. I can't place anything into the folder.
I'm using the following command to mount the share:

```
//192.168.1.160/Guest\040Share /mnt/backup/ cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

And my SMB.conf file:
```

[global]
workgroup = BACKUP
server string = Backup System
security = share
guest account = nobody
log file = /var/log/samba.%m
usershare allow guests = yes

[Guest Share]
        comment = Redundant Backup
        path = /home/samba
        browseable = yes
        writable = yes
        read only = no
        guest only = yes
        create mask = 0775
        directory mask = 0775
        force create = 0775
        force directory mask = 0775

```

I think the problem is with the way I'm mounting the share on my Ubuntu machines. If I go to the share using smb://192.168.1.160 in a file browser, I can create new folders which are readable and writable by everyone. But, if I create the new folder where it's mounted at /mnt/backup, no-one can modify or change it.

Any help would be much appreciated!! :D

---

### Post by cian1500ww on 2011-04-24
I found a solution to my problem, I added uid=1000 to the mount command in the fstab, this gave my user full permissions over the mounted share.

The mount command that worked was:
```
//192.168.1.160/Guest\040Share /mnt/backup/ cifs guest,uid=1000,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
```

---

### Post by Paddy Landau on 2011-04-24
Thank you for posting your solution. This should help some people.

---
Please mark your thread as Solved.

---

