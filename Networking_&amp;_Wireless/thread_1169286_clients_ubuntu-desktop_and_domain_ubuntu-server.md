---
title: "clients ubuntu-desktop and domain ubuntu-server"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by W03L on 2009-05-25
Hi.
There is a problem:
I can't logon on client PC (ubuntu) under domain account (ubuntu) (no user found). If I logon under local account and try to open a share on server it ask to enter user name and password, after that share is open (use domain user account and password).
Also I'm try to use windows as client of the same domain - it's all ok.

smb.conf on domain
```
[global]
	workgroup = STUD.RU
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad Password
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = wins bcast hosts lmhosts
	time server = Yes
	add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
	delete user script = /usr/sbin/userdel -r %u
	add group script = /usr/sbin/groupadd %g
	delete group script = /usr/sbin/groupdel %g
	add user to group script = /usr/sbin/usernod -G %g %u
	add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody -g comps %u
	logon script = logon.cmd
	logon path = \\uStud\profiles\%U
	logon drive = Z:
	logon home = \\uStud\homes\%U
	domain logons = Yes
	preferred master = Yes
	domain master = Yes
	wins support = Yes
	message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
	panic action = /usr/share/samba/panic-action %d
	idmap uid = 15000-20000
	idmap gid = 15000-20000
	template shell = /bin/bash
	admin users = root administrator
	guest ok = Yes

[public]
	comment = common
	path = /media/sdd1/all
	read only = No

[homes]
	comment = Home
	path = /media/sdd1/homes
	valid users = %S
	read only = No
	create mask = 0755
	browseable = No

[netlogon]
	comment = Network Logon Service
	path = /media/sdd1/netlogon
	valid users = %U
	admin users = administrator root
	browseable = No
	share modes = No

[profiles]
	comment = User profiles
	path = /media/sdd1/profiles
	valid users = %U
	read only = No
	create mask = 0775
	directory mask = 0775
	guest ok = No
	browseable = No
```

smb.conf on client
```
[global]
	workgroup = stud.ru
	netbios name = PC
	realm = stud.ru
	password server = uStud.stud.ru
	domain master = no
	template homedir = /home/stud/%U
	template shell = /bin/bash
	winbind use default domain = yes
	server string = %h client (Samba, Ubuntu)
	dns proxy = no
	name resolve order = lmhosts host wins bcast
	log file = /var/log/samba/log.%m
	max log size = 1000
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	security = domain
	encrypt passwords = true
	passdb backend = tdbsam
	obey pam restrictions = yes
	unix password sync = no
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	pam password change = no
	map to guest = bad user
	socket options = TCP_NODELAY
	idmap uid = 10000-20000
	idmap gid = 10000-20000
	winbind enum groups = yes
	winbind enum users = yes
	usershare max shares = 100
	usershare allow guests = yes
```

---

### Post by lisati on 2009-05-25
Although one might not expect it to make a difference, I notice you've got the workgroup capitalised in one file, and lower case in the other.

---

### Post by W03L on 2009-05-25
> **lisati said:**
> Although one might not expect it to make a difference, I notice you've got the workgroup capitalised in one file, and lower case in the other.

change to upper case - no result

---

