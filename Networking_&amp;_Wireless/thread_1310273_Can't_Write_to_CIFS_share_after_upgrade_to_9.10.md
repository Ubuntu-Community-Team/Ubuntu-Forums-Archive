---
title: "Can't Write to CIFS share after upgrade to 9.10"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by nexist on 2009-11-01
My home network has a file server running Ubuntu server. I have my desktop attached to it via a SAMBA/CIFS share which just mounts my home directory on that system (obelisk) as a directory for my desktop. I could read/write to the dir with no problems. Both were running 9.04.  I the desktop to 9.10 today and I find that I can no longer write to my home directory through the share.  My work laptop, running Windows Vista, can connect and write to the share.

The relevant line in my fstab is:

```
# Samba share on obelisk
//10.11.93.2/nexist /home/nexist/obelisk cifs username=nexist,password=****,nounix,iocharset=utf8   0 0
```

Can anyone tell me what changed with the Samba/CIFS that would cause this behavior?

---

### Post by cotillion2009 on 2009-11-03
Having the same problem. cifs-shares mounted via fstab or mount.cifs are always read-only.
When mounting through gnome.vfat read-write-access is possible.

Any suggestions?

---

### Post by The_CableGuy on 2009-11-09
I have the same problem with cifs share. Only read, no write.
The mount worked fine in 9.04.
Is this a bug?

---

### Post by dmizer on 2009-11-10
I've posted a fix for this in my howto (2nd link in my sig). It's listed under: KARMIC: Files owned by root / "The folder contents could not be displayed"

---

### Post by nexist on 2009-11-11
> **dmizer said:**
> I've posted a fix for this in my howto (2nd link in my sig). It's listed under: KARMIC: Files owned by root / "The folder contents could not be displayed"

This did not fix my problem. I still cannot access my Samba share (9.04) in rw mode from my Desktop (9.10).

---

### Post by dmizer on 2009-11-11
> **nexist said:**
> This did not fix my problem. I still cannot access my Samba share (9.04) in rw mode from my Desktop (9.10).

Okay, then try the fix labeled
> Files owned by root / "The folder contents could not be displayed"

If that still does not work, please post your current /etc/fstab line, as well as the output of:
```
sudo iptables -L
```

---

### Post by nexist on 2009-11-13
Here is the fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=f736b56c-870a-45dd-8a2d-fc8cc8b220ed /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=ba58f240-fec8-4f0d-be43-4efbbf169d88 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
# Samba share on obelisk
//10.11.93.2/nexist /home/nexist/obelisk cifs username=nexist,password=******,nounix,iocharset=utf8,noserverino   0 0
#
# For USB access with Virtualbox
none	/proc/bus/usb	usbfs	devgid=126,devmode=664	0  0
```

and the output of sudo iptables -L
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
```

Thank you.

---

### Post by cakper on 2009-11-13
Try with this options added at the end:
```
,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

---

### Post by dmizer on 2009-11-13
You'll need to add the uid and gid options like so:


1) Find your uid and gid (normally both are 1000, but double check):
```
cat /etc/passwd | grep nexist
```
The output will look something like this (my uid and gid are marked in red):
```
$ cat /etc/passwd | grep dmizer
dmizer:x:[COLOR="Red"]1000[/COLOR]:[COLOR="Red"]1000[/COLOR]:dmizer,,,:/home/dmizer:/bin/bash
```

2) Add gid, uid, and nounix options to your fstab line like so:
```
 //10.11.93.2/nexist /home/nexist/obelisk       cifs    username=nexist,password=******,iocharset=utf8,[COLOR="Red"]gid=1000,uid=1000,nounix[/COLOR],noserverino,file_mode=0777,dir_mode=0777 0 0
```

---

### Post by nexist on 2009-11-13
That has fixed it. Thank you very much.

---

### Post by duartemolha on 2009-11-19
I am still having problems... I've searched for all options and I've tried ALL of them...

The weird thing is that gedit and open-office can save and edit all files in the cifs mounted drives but all other programs cannot.

If I open a text file in lets say "Padre" text editor or Komodo... they fail to save the files edited in them...

Can anyone tell me what is wrong?

I did not have this problem in 9.04... only after updating to 9.10

It is very frustrating.

Best regards, 

      Duarte

---

### Post by dmizer on 2009-11-19
> **duartemolha said:**
> I am still having problems... I've searched for all options and I've tried ALL of them...

Please post your current /etc/fstab line.

---

### Post by duartemolha on 2009-11-20
Here are the lines for mounting the remote  drives of my fstab:

```
//192.168.0.223/duartem		/media/dell_home	cifs	defaults,credentials=/root/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,nounix,noserverino,file_mode=0777,dir_mode=0777 0 0
//192.168.0.223/project 	/media/project		cifs	defaults,credentials=/root/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,nounix,noserverino,file_mode=0777,dir_mode=0777 0 0
//192.168.0.223/services 	/media/services		cifs	defaults,credentials=/root/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,nounix,noserverino,file_mode=0777,dir_mode=0777 0 0
//192.168.0.223/dept 		/media/dept 		cifs  	defaults,credentials=/root/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,nounix,noserverino,file_mode=0777,dir_mode=0777 0 0
//ABYSS/Public 		/media/public 		cifs  	defaults,credentials=/root/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,nounix,noserverino,file_mode=0777,dir_mode=0777 0 0
//192.168.0.223/seqdata 	/media/seqdata 		cifs  	defaults,credentials=/root/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,nounix,noserverino,file_mode=0777,dir_mode=0777 0 0
//192.168.0.223/archive 	/media/archive 		cifs  	defaults,credentials=/root/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,nounix,noserverino,file_mode=0777,dir_mode=0777 0 0
```


Anything wrong with this?

Cheers, 

     Duarte

---

### Post by Max-Ulrich on 2010-01-07
>gid=1000,uid=1000,n  ounix,noserverino,file_mode=0777,dir_mode=0777 0 0

It should be `nounix`, not `n ounix`.

Best Regards, Max-Ulrich

---

### Post by dmizer on 2010-01-07
> **duartemolha said:**
> Here are the lines for mounting the remote  drives of my fstab:

```
//192.168.0.223/duartem		/media/dell_home	cifs	defaults,credentials=/root/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,nounix,noserverino,file_mode=0777,dir_mode=0777 0 0
//192.168.0.223/project 	/media/project		cifs	defaults,credentials=/root/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,nounix,noserverino,file_mode=0777,dir_mode=0777 0 0
//192.168.0.223/services 	/media/services		cifs	defaults,credentials=/root/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,nounix,noserverino,file_mode=0777,dir_mode=0777 0 0
//192.168.0.223/dept 		/media/dept 		cifs  	defaults,credentials=/root/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,nounix,noserverino,file_mode=0777,dir_mode=0777 0 0
//ABYSS/Public 		/media/public 		cifs  	defaults,credentials=/root/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,nounix,noserverino,file_mode=0777,dir_mode=0777 0 0
//192.168.0.223/seqdata 	/media/seqdata 		cifs  	defaults,credentials=/root/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,nounix,noserverino,file_mode=0777,dir_mode=0777 0 0
//192.168.0.223/archive 	/media/archive 		cifs  	defaults,credentials=/root/.smbcredentials,iocharset=utf8,gid=1000,uid=1000,nounix,noserverino,file_mode=0777,dir_mode=0777 0 0
```


Anything wrong with this?

Cheers, 

     Duarte

You cannot write to any of those at all?

---

### Post by japher on 2010-03-31
You need to add **noperm** to the list of options. I had exactly the same problem when moving to 9.10, and the noperm option fixed it.

---

