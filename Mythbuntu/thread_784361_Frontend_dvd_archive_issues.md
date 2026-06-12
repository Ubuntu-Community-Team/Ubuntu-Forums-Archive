---
title: "Frontend dvd archive issues"
date: 2008-05-06
forum: Mythbuntu
---

### Post by apauna on 2008-05-06
Hello,

When I attempt to burn a DVD from my frontend PC it cannot find any of the recordings that are stored on the backend server. 

So then I used smbfs to mount the server recordings to the frontend recordings location /var/lib/mythtv/recordings and then I could access the recordings from the DVD archive feature, but then live tv playback ceased to function correctly. 

So I took the lesser of two evils and have removed the smbfs mount. This, of course, means that I can no longer archive my recordings from a frontend.

Any suggestions on how to get around this problem?
Is this a bug in myth or a bad config on my part?

I choose smb instead of nfs because it seemed to be more secure of a solution allowing me to set a user and password. Maybe NFS is better and I just do not understand how to set it up correctly.

Thanks,
Al

---

### Post by IanW on 2008-05-06
If it helps, I used /etc/fstab to mount my smb shares to directories inside /var/lib/mythtv

---

### Post by apauna on 2008-05-06
> **IanW said:**
> If it helps, I used /etc/fstab to mount my smb shares to directories inside /var/lib/mythtv

I did that as well here is my fstab:
```
# /etc/fstab: static file system information.

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3ed4113c-2d0c-47c2-a1af-3099edfdde2d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ce2b9cf7-802b-4fe1-889f-5c5fd2528a7b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

//192.168.1.11/music  /var/lib/mythtv/music  smbfs uid=1000,dir_mode=0776,file_mode=0776,credentials=/root/.smbpasswd,gid=1000  0  0
//192.168.1.11/videos  /var/lib/mythtv/videos  smbfs uid=1000,dir_mode=0776,file_mode=0776,credentials=/root/.smbpasswd,gid=1000  0  0
//192.168.1.11/pictures  /var/lib/mythtv/pictures  smbfs uid=1000,dir_mode=0776,file_mode=0776,credentials=/root/.smbpasswd,gid=1000  0  0


```

problems occur if I try that with /var/lib/mythtv/recordings :confused:

---

### Post by apauna on 2008-05-06
BTW: this is Mythbutu 8.04.

---

