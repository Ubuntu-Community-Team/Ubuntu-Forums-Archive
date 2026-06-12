---
title: "XP cannot access a nautilus share"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by nightskywind83 on 2010-02-21
Hi all,

This could be something totally obvious, but I've tried what I can so far.  I have an XP box on my network that needs to access a shared folder on my ubuntu box.  I own the folder, and I right click and click "Sharing options" and then check "Share this folder" and "guest access."  I go over to my XP box and in Network neighborhood I can see the folder(s) that I have shared from Ubuntu, but when I double click I get an error message that "\\server\folder" is not accessible, you may not have permission, etc etc"   I've tried setting it up through Samba as well with no luck.  This seems like it should be simpler, but I'm ready to pull my hair out.  Please have mercy on my noobish ways and help me! lol

---

### Post by nightskywind83 on 2010-02-21
*smacks forehead* I'm running ubuntu 9.10, and heres a post of some useful info:
[B]
# net usershare info[/B] - 
[tmpbu]
path=/media/backup/tmpbu
comment=
usershare_acl=Everyone:F,
guest_ok=y

[jessbu]
path=/media/storage/jessbu
comment=
usershare_acl=Everyone:R,
guest_ok=y

**testparm -s**

Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	lanman auth = Yes
	client lanman auth = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = lmhosts host wins bcast
	dns proxy = No
	usershare allow guests = Yes
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	guest ok = Yes
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	guest ok = Yes

---

### Post by Morbius1 on 2010-02-21
Please post the output of the following commands:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**

It sounds like a linux file permissions problem not a samba problem.
[COLOR=Blue]
EDIT: You read my mind.[/COLOR]

---

### Post by Morbius1 on 2010-02-21
Open **Terminal**
Type **ls -dl /media/backup/tmpbu**
Type **ls -dl /media/storage/jessbu**

I think this could have an easy fix.

---

### Post by nightskywind83 on 2010-02-21
**ls -dl /media/backup/tmpbu**

drwxrwxrwx 11 nobody nogroup 4096 2010-02-20 23:22 /media/backup/tmpbu

**ls -dl /media/storage/jessbu**

drwxr-xrwx 6 phuxx0r3d phuxx0r3d 20480 2009-10-20 17:15 /media/storage/jessbu

---

### Post by Morbius1 on 2010-02-21
Well, I thought this was going to be an easy fix but unfortunately the linux permissions on those directories look correct for what you want to do.

The first thing I would check are the parent directories permissions. You meed to have read access enabled on /media/storage and /media/backup.

[B]ls -dl /media/storage
ls -dl /media/backup[/B]

---

### Post by nightskywind83 on 2010-02-21
**ls -dl /media/storage**
drwx------ 14 phuxx0r3d phuxx0r3d 4096 2010-01-20 08:27 /media/storage

 **ls -dl /media/backup**
drwxrw-rw- 4 phuxx0r3d phuxx0r3d 4096 2010-02-17 09:10 /media/backup

---

### Post by Morbius1 on 2010-02-21
That I think is the problem. The easiest fix since you're sharing through nautilus is to try this:

Open **Terminal**
Type **gedit /etc/samba/smb.conf**

Add the following line to the [COLOR=Blue][global][/COLOR] section of smb.conf:

```
 force user = phuxx0r3d
```

Save the file, exit gedit, and back in the terminal type: **sudo service samba restart**

---

### Post by nightskywind83 on 2010-02-21
this solved the problem for "jessbu" but "tmpbu" still has the same error.

If we relook at the net usershare info output, would the line "usershare_acl=Everyone:F," cause this issue?  it's the only difference i see.  I chown'ed /media/backup to phuxxor3d.

Interestingly, if I go into XP, view workgroup computers, under the ubuntu box the only folder that shows up is "jessbu"

---

### Post by Morbius1 on 2010-02-21
>  "usershare_acl=Everyone:FThat just means you're allowing write access to that share.

When I first saw this:
> **ls -dl /media/backup/tmpbu**

drwxrwxrwx 11 nobody nogroup 4096 2010-02-20 23:22 /media/backup/tmpbuI thought that was kind of strange that a folder got created with owner = nobody. But since the permissions where set to universal access I just ignored it.

I really don't think that's the problem but you might want to chown /media/backup/tmpbu to phuxx0r3d

---

### Post by nightskywind83 on 2010-02-21
Haha.  That nobody ownership was a result of trying to get this to work.  I've been all over ubuntu, samba, and other websites reading all kinds of information.  I changed the "tmpbu" folder ownership specifically as you suggested and that did the trick.  thanks for your help :)

---

