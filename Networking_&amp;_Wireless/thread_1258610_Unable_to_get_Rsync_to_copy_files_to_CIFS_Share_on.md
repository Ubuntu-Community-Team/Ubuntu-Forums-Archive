---
title: "Unable to get Rsync to copy files to CIFS Share on NAS"
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by pjaikins on 2009-09-05
Ok, here's the situation. I'm running Jaunty and have a Qnap NAS drive. I have mapped the various shares with the following in /etc/fstab:
//10.0.0.3/Public /media/public cifs auto,credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777,nosuids,noperms,rw,exec 0 0
//10.0.0.3/Qmultimedia /media/multimedia cifs auto,credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777,nosuids,noperms,rw,exec 0 0
//10.0.0.3/Qdownload /media/download cifs auto,credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777,nosuids,noperms,rw,exec 0 0
//10.0.0.3/Backup /media/backup cifs auto,credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777,nosuids,noperms,rw,exec 0 0
//10.0.0.3/Qusb /media/qusb cifs auto,credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777,nosuids,noperms,rw,exec 0 0

This all works fine and I can read and write files to and from these shares without any problems until I try to use rsync based backup tools like "Back in Time" or "Flyback'. They all report permission denied errors and simply just copy the directories to the shares, but not the files. 
I have unmounted the shares and ensured that all the directories they are mapped to in the /media directory have absolute permissions of 777 but to now avail. If I run the same programs, but with the destination as a local directory, they run perfectly. Can someone please explain how I fix this as surely mine is not an uncommon requirement.:confused:

---

