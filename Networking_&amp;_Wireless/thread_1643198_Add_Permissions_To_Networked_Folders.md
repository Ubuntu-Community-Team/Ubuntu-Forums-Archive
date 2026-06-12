---
title: "Add Permissions To Networked Folders"
date: 2010-12-11
forum: Networking &amp; Wireless
---

### Post by DeMartini on 2010-12-11
Ok here is the deal, I am allowing my neighbor access to some networked folders on my ubuntu file server in exchange for access to their washer & dryer. I have already created mapped drives on their xp machines but now I want to only allow them "read only" access so they don't accidentally delete anything?

---

### Post by Morbius1 on 2010-12-11
Why not post your smb.conf file so we can see how your are set up:
```
testparm -s
```

---

### Post by DeMartini on 2010-12-11
> **Morbius1 said:**
> Why not post your smb.conf file so we can see how your are set up:
```
testparm -s
```

Here you are:


Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

---

### Post by Morbius1 on 2010-12-11
Well, you don't have any Samba Classic Shares defined so maybe you're using Samba Userhsres. Please post the output of this command:
```
net usershare info --long
```

---

### Post by DeMartini on 2010-12-11
> **Morbius1 said:**
> Well, you don't have any Samba Classic Shares defined so maybe you're using Samba Userhsres. Please post the output of this command:
```
net usershare info --long
```

Here we are:

[music]
path=/home/jamie/Music
comment=
usershare_acl=Everyone:F,
guest_ok=y

[p90x]
path=/home/jamie/P90X
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/linux study  is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[videos]
path=/home/jamie/Videos
comment=
usershare_acl=Everyone:F,
guest_ok=n

[pictures]
path=/home/jamie/Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=n

[documents]
path=/home/jamie/Documents
comment=
usershare_acl=Everyone:R,
guest_ok=y

jamie@jamie-laptop:~$

---

### Post by Morbius1 on 2010-12-11
All of your shares will allow read / write access except  [documents]. For all those shares that you want to make read only just go back into Nautilus and uncheck the following option:
> Allow others to create and delete files in this folder

---

### Post by DeMartini on 2010-12-11
Thanks for your help, I should have see that option.

---

