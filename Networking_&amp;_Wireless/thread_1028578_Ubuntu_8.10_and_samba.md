---
title: "Ubuntu 8.10 and samba"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by valkoapina on 2009-01-02
Hi,

I have some problems setting up samba correctly in ubuntu 8.10. I have installed 2:3.2.3-1ubuntu3.3 package and it seems to run fine, but when I try to access shares from win xp box, it's a no go. My ubuntu box shows in network places under workgroup, but when I try to access it, I get a response that path does not exist or I might not have appropriate priviliges. Also trying to access the shares straight with "\\IP-address\username\" does not work. I have succesfully set-up samba to previous versions of ubuntu and debian, but for some reason I cannot get it to work with 8.10.

---

### Post by valkoapina on 2009-01-02
Here is my testparm output:

```
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	server string = %h server (Samba, Ubuntu)
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
	panic action = /usr/share/samba/panic-action %d

[homes]
	comment = Home Directories
	valid users = %S
	create mask = 0700
	directory mask = 0700

```

---

### Post by valkoapina on 2009-01-02
Never mind, firestarter had started firewall again. Sorry for spam.

---

