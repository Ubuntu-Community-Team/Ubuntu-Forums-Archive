---
title: "mount via cifs does not show all files - smb does"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by twinkler on 2010-01-09
Dear all,

I have got my MP3 collection on a NAS (a CISCO NSLU2) on a share called media. I am running ubuntu 9.10.

Mapping it in Windows XP works fine.
Browsing it in Nautilus via SMB (I guess?) works fine too.

But when I mount it I can only see the directories starting with "h", everything else is not visible. When I create new directories/files from other machines I can not see these files in Linux. It is almost if mount created a snaphshot which does not get refreshed anymore. 

I am positive though that all machines using the same username and password when accessing the share.

The entry in my fstab is as following:

//192.168.178.29/media /home/torsten/NAS/media cifs user=media,password=xxx,user,noauto,iocharset=utf8,gid=1000,uid=1000,nounix,file_mode=0777,dir_mode=0777 0 0

Does anyone have an idea? Any hints are appreciated

Cheers

Torsten

---

### Post by dmizer on 2010-01-09
Please post the output of:
```
sudo ls -la /home/torsten/NAS/media
```

Also, do you get the same problem if you remove the "user" option, so your mount line will look like this:
```
//192.168.178.29/media /home/torsten/NAS/media cifs user=xxxx,password=xxx,noauto,iocharset=utf8,gid=1000,uid=1000,nounix,file_mode=0777,dir_mode=0777 0 0
```

---

### Post by twinkler on 2010-01-10
the output of the ls command as superuser is

```

drwxrwxrwx 365 torsten torsten    0 2010-01-10 00:36 .
drwxr-xr-x   3 torsten torsten 4096 2010-01-08 20:41 ..
drwxrwxrwx   3 torsten torsten    0 2010-01-09 04:16 2005_Rainald Grebe & die Kapelle der Versöhnung
drwxrwxrwx   4 torsten torsten    0 2010-01-09 04:15 2raumwohnung
drwxrwxrwx   5 torsten torsten    0 2010-01-09 04:16 3 Doors down
drwxrwxrwx   3 torsten torsten    0 2010-01-09 04:16 59 Times The Pain


``` 

ad so on. I can see all directories until they start with "H"

When I remove the "user" option and mount the share as root the behaviour is exactly the same. It is really strange....

Cheers

Torsten

---

### Post by dmizer on 2010-01-10
Well, I'm trying to see exactly what the CLI says about your h lettered directories. Have you tried renaming one or two of them (I mean, rename it to the same name)?

Try this:
```
sudo ls -la /home/torsten/NAS/media/h*
```

---

