---
title: "smb usershare asks for credentials"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by wensveen on 2009-12-24
Hi,

I'm trying to share my 'Public' folder to several other computers in my local network with Karmic. This has always worked with previous installations of ubuntu but I've recently reinstalled my machine with Karmic.

The problem is that when I try to access the share from a windows machine, it asks for credentials. Any sting as a username and an empty password will work. Unfortunately my xbox media center doesn't ask anything and just rejects the connection.
Strangely, another machine running ubuntu (Jaunty) is able to browse the share without asking for credentials.

Some relevant information:
```
matthijs@cerebro:~$ net usershare info
[public]
path=/home/matthijs/Public
comment=
usershare_acl=Everyone:R,
guest_ok=y
```

```
matthijs@cerebro:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
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
```

I'd be very grateful if someone can help me fix this and I can watch movies and listen to music with my xbox again.

Regards,
Matthijs

---

