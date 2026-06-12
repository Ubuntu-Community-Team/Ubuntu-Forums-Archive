---
title: "Question for Samba file for PDC Server."
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by voncloft on 2009-03-04
Below is my samba file for my ubuntu desktop i am using it as a Primary Domain Controller for windows xp  clients to login to. I was just wondering if anyone can see anything thats wrong with it.  The only thing that is not working is the csc policy = disable, the xp computers still cache to their own hard drive.   If anyone can see some tweaks, threats, problems, or some real cool stuff to add to the file let me know.

---------------------------------------------------------------------

# Samba config file created using SWAT
# from UNKNOWN (˜·ô¿©·èã¹ÐŠ‰·ÈÃ¿W¡£·èã¹Ã§ü·äÃ¿)
# Date: 2009/02/09 03:53:44

[global]
	
	netbios name = VSERV
	Workgroup = VDOMAIN
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	smb passwd file = etc/samba/smbpasswd
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	password level = 8
	username level = 8
	unix password sync = Yes
	log level = 3
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	add user script = /usr/sbin/adduser -n -g machines -c Machine -d /dev/null -s /bin/false %m$
	logon script = logon.bat
	logon path = \\vserv\profiles\%U
	domain logons = Yes
	os level = 64
	domain master = Yes
	dns proxy = No
	wins support = Yes
	default service = homes
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	hosts allow = 192.168.1.0/16
	printing = lprng
	print command = lpr -r -P'%p' %s
	lpq command = lpq -P'%p'
	lprm command = lprm -P'%p' %j
	lppause command = lpc hold '%p' %j
	lpresume command = lpc release '%p' %j
	queuepause command = lpc stop '%p'
	queueresume command = lpc start '%p'
	dont descend = /media
	browse list = yes
	printcap name = cups
	printing = cups
	load printers = yes
	

[homes]
	comment = Home Directories
	path = /home/%u
	read only = No
	guest ok = Yes
	csc policy = disable

[media]
	comment = Nick's Share
	path = /media
	valid users = nick, @nick
	read only = No
	guest ok = no

[netlogon]
	path = /home/netlogon
	write list = admin
	guest ok = Yes
	browseable = Yes

[public]
	path = /home/public
	read only = No
	create mask = 0777
	guest ok = Yes

[profiles]
	csc policy = disable
	comment = Network Profiles Share
	path = /etc/samba/profiles
	read only = No
	create mask = 0600
	directory mask = 0700
	profile acls = Yes
	store dos attributes = Yes
	browseable = No
	guest ok = Yes
	hide files = /desktop.ini/outlook*.lnk/*Briefcase*/

---

