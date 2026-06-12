---
title: "Can't write to Windows share after mounting"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by clevertomato on 2009-11-20
I have been using basic mount commands for a while to mount my FreeNAS via CIFS, but now I'm trying to mount a Windows share and cannot write to it. The FreeNAS box has anonymous CIFS access enabled. The Windows share is on a 64-bit XP box. I've tried various mount options, but the latest, most comprehensive is:
```

sudo mount -t cifs //192.168.0.20/sharename ./mymnt -o user=myusrname,pass=mypassword,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
```I've also tried using -t smbfs as well as uid=xxxx,gid=xxxx with no success.

Can anybody help? I discovered the problem while trying to use FSarchiver on the sysrescue cd to backup partitions over my LAN, but then I discovered I can't get it to work on my other PC running Ubuntu Karmic.

---

### Post by mattlindsay on 2009-11-20
Try looking here:
 
[http://ubuntuforums.org/showthread.php?t=1329753](http://ubuntuforums.org/showthread.php?t=1329753)

---

### Post by clevertomato on 2009-11-20
I did three things... I'm not sure which fixed it but it works now and I don't have time to mess with finding out at the moment.

1) On my XP box, I enabled "allow other users to change files."
2) In the mount command I changed user to username and pass to password, then
3) I put my actual username and password in double quotes thusly:

sudo mount -t cifs //192.168.0.20/sharename ./mymnt -o username="myusrname",password="mypassword",rw,iocharset=utf8,file_mode=0777,dir_mode=0777
-- Solved --

---

