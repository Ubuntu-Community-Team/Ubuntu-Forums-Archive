---
title: "access denied on samba share after karmic upgrade"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by vayu on 2009-11-16
After upgrading to karmic I get an "access denied" error when trying to write to a samba share.

From the Karmic machine I can see the files on the windows machine but when I try to drag a file from a Karmic directory to a Windows directory it gives the error.  I can drag a file from the Windows directory to the Karmic directory.  On the Windows machine I can copy both ways no problem.

This is the command I've been using for 9.04.  Has anything changed that I need to update smb.conf or the mount syntax?

```
sudo mount //10.0.0.20/wwwroot$ /home/satyam/shares/prajipati/www/ -o username=satyam,password=mypassword,dmask=777,fmask=777

```

---

### Post by dmizer on 2009-11-16
There is a fix for this located in the troubleshooting section of my CIFS tutorial (2nd link in my sig)

---

### Post by vayu on 2009-12-08
> **dmizer said:**
> There is a fix for this located in the troubleshooting section of my CIFS tutorial (2nd link in my sig)

Thanks much, that worked.

---

### Post by vayu on 2009-12-11
Ok that gave my Ubuntu computer access to the XP computer but now the XP computer lost the name access to the Ubuntu computer.  I can find the Ubuntu's IP address with ifconfig and then Windows will be able to access it as \\10.0.0.xxx.  What do I do to get the Ubuntu name (akasha) to work for windows?

Here's what I think are the relevant parts of smb.conf

```
   workgroup = vayu
   netbios name = akasha
   server string = %h server (Samba, Ubuntu)
#   wins support = no
;   wins server = w.x.y.z
   dns proxy = no
   name resolve order = lmhosts wins bcast host

[FAT32]
	comment = Akasha/mnt/fat32
	path = /mnt/fat32
;	browseable = yes
	writeable = yes
	valid users = satyam
	create mask = 0775
	directory mask = 0775

```

---

