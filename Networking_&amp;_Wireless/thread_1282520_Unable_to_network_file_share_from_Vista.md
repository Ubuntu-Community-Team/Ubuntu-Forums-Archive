---
title: "Unable to network file share from Vista"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by jcobban on 2009-10-04
I have just acquired a new laptop running Vista, an operating system with which I am not familiar but which, for the moment at least, I would prefer not to just discard since I still have one app that works better on Windows than on Linux.  As a basic form of backup I would like to copy all of my user files from my Ubuntu desktop onto the laptop.  While I can see all of the files on the Laptop from Ubuntu, the folders are currently read only, so unless I change the Vista config (which I haven't learned how to do yet), I will have to open the Ubuntu folders from Vista.

I have configured SAMBA with the following configuration file:

[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog only = Yes
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	wins support = Yes
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[homes]
	comment = Home Directories
	valid users = %S
	create mask = 0600
	directory mask = 0700
	browseable = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

My Ubuntu system appears in the Vista network view, but when I try to connect to it I get a logon unsuccessful message.  I note that although I entered my userid and password, when the error dialog is displayed, the User Name field in the Connect dialog has been changed to "laptop-name\userid".  If that is what Vista is sending to Ubuntu, it is not a surprise that it is rejected.

The advice that I can find on the web is contradictory as to what is to be set in smb.conf, and in many cases only describes working with Windows XP.

---

