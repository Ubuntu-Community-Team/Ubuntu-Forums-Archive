---
title: "How can I share media from ubuntu 13.04 to windows XP"
date: 2013-09-26
forum: Multimedia Software
---

### Post by bsamim on 2013-09-26
So I have set up samba successfully and I am using it for file shares but when trying to do media shares I am having issues. Specifically the problem is that I can see the Media folder in Windows but then I can't go into them. I get permission denied. I have changed the /media/username to soft link to a /media/share folder and this is working. The problem is that the file system won't let me change perms on a media directory item even as root. As a result, I am trying to see if anyone else is sharing their media from a linux machine to a windows machine. See below my attempt to change the directory perms. My Passport is a WD external hard drive. I can see the My Passport folder in Windows I just can't open it.

```
soft link:


root@BigJackFly:/media# ls -ltr
total 4
lrwxrwxrwx 1 root   root       5 Sep 25 18:41 bjackfly -> share
drwxr-xr-x 4 nobody nogroup 4096 Sep 25 20:48 share




root@BigJackFly:/media/share# chmod 777 My\ Passport/
root@BigJackFly:/media/share# ls -ltr


drwx------ 1 bjackfly bjackfly 4096 Sep 25 21:04 My Passport


smb.conf
[mediashare]
   comment = Public Stuff
   path = /media/share
   browseable = yes
   guest ok = yes
   read only = no
   create mask = 0775

```

---

