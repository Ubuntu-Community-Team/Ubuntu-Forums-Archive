---
title: "Samba password protected folders problem"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by dead_arhip on 2009-12-01
Hi,

I have Ubuntu 9.04 Server. It's sharing several folders. Some of them are "opened" for rw for everyone. Also there are password protected folders.  
The problem is that it takes too much time to login into password protected folder from Windows XP machine. There are no other problems.

So, when i click to password protected folder, explorer hangs up and
logon dialog appears only after 1-2 minutes. Then I log in and everything ok.

Thank you.


My smb.conf:

[global]
	workgroup = OBERON
	server string = %h server (Samba, Ubuntu)
	interfaces = 127.0.0.0/8, eth0
	bind interfaces only = Yes
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
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
	invalid users = root

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[data]
	path = /mnt/data
	valid users = alex
	read only = No

[o]
	path = /mnt/data/common
	read only = No
	guest ok = Yes

[reports]
	path = /mnt/data/reports/all
	guest ok = Yes

[pv]
	path = /mnt/data/pv
	valid users = pv
	read only = No

---

