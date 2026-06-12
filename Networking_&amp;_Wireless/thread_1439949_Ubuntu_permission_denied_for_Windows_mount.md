---
title: "Ubuntu permission denied for Windows mount"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by David.Levin on 2010-03-26
Ok, so I have followed that many post about using a Windows mount, and still have an issue.

Using Ubuntu 8.04 to mount a shared on a Windows 2003 Server.

I have the fstab method with this line:

//server/xms /mnt/xms cifs defaults,uid=1000,gid=1000,credentials=/root/.smbcredentials 0 0 

or

//server/xms /mnt/xms cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

both work when doing a mount /mnt/xms command.  I can ls the directory on the windows share.  I can cat files from the windows share.

If I touch or mkdir in the windows share I get "Permission denied"


Please help me out of cifs hell.

Thanks,
David

---

### Post by Iowan on 2010-03-27
Who is the owner of the share (as far as **ls** is concerned)?

---

### Post by David.Levin on 2010-04-02
user and group and both administrator administrator

---

