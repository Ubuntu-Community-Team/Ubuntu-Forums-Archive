---
title: "Accessing windows share  results in corruputed files."
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by gdk on 2010-08-19
I've got a problem accessing my windows shares from ubuntu 9.10. Everything works good, but then I can't read updated files from the share properly on ubuntu.
 
The fstab entry is as follows:
//192.168.0.6/linuxshare /mnt/pc smbfs user=Administrator,dir_mode=0777,file_mode=0777,rw,noauto,iocharset=utf8,sync 0 0
 
 
Here is the scenario.
 
1) On my windows XP box, copy a file to the windows share folder. Lets call it xyz.txt.
2) On the Ubuntu 9.10 box, copy the file xyz.txt from the mount point (/mnt/pc/xyz.txt) to say /tmp.
3) Everything is fine to here. Now go back to the windows box and copy a new version of xyz.txt to the share folder. Lets say that xyz.txt is 100 bytes longer with some new text.
4) Now on the Ubuntu box, repeat step 2. This time the file in /mnt/pc/xyz.txt is NOT the new version of the file. Ubuntu is seeing a mixed up file between the old version and the new version. For example, the contents appears to be the old version of the file. But then it loads up a bunch of NULLS at the end of the file.
 
I've tried cifs and smbfs. No luck. This does NOT happen all the time. But once it does, it's screwed. If I umount/mount it, everything is good again. It's like Ubuntu is caching the old file or something.
 
Anyone got a solution for me? It's driving me nuts!
 
Thanks.

---

