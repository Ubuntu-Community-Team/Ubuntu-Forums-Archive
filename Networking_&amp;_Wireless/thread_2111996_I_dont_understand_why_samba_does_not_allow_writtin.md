---
title: "I dont understand why samba does not allow writting"
date: 2013-02-03
forum: Networking &amp; Wireless
---

### Post by Hugolp on 2013-02-03
Hi

I have been setting up a samba share for an android stick that I use as media center. I have been reading on Samba to set it up properly, I can connect and access the files but I can not write/delete them. I know that to be able to write I need write permission at the samba level and at the linux permission level.

I have the user linaro (group linaro) which has permissions on the folders and files shared. I log in as linaro but can not delete files. Here are a testparm and the linux permissions, I really dont understand where it goes wrong:

```

linaro@linaro-ubuntu-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[shared]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	interfaces = 127.0.0.0/8, eth0
	bind interfaces only = Yes
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
	idmap config * : backend = tdb

[shared]
	comment = Shared
	path = /mnt/datadisk/shared
	valid users = linaro
	write list = linaro
	read only = No
	create mask = 0775
	directory mask = 0775

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
linaro@linaro-ubuntu-desktop:~$ 
```

```
linaro@linaro-ubuntu-desktop:/mnt/datadisk/shared$ ls -la
total 24
drwxrwxr-x  6 linaro              linaro              4096 Jan 31 18:33 .
drwxrwxr-x  5 linaro              linaro              4096 Feb  3 14:12 ..
drwxrwxr-x  4 linaro              linaro              4096 Jan 31 14:42 comics
drwxrwxr-x 26 linaro              linaro              4096 Jan 20 13:03 music
drwxrwxr-x  4 linaro              linaro              4096 Jan 31 18:33 video
linaro@linaro-ubuntu-desktop:/mnt/datadisk/shared$ 
```

Thanks in advance

---

### Post by Hugolp on 2013-02-04
Bumb, can anyone help?

---

