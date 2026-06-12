---
title: "Samba domain server how do I add ubuntu desktop as a client"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by voncloft on 2009-11-20
I would like to add my Ubuntu 9.1 Desktop to my Domain since I am constantly reinstalling Ubuntu from scratch when a new distro comes out and would like to have my user accounts saved to the server so I can retrieve them from the server without having to remake user preferences on the client each time I install linux. Below is my configuration of my samba server that will allow windows machines to login to my domain via username on password at the login screen.  How exactly would I be able to add my Ubuntu 9.1 Desktop to this server.  I tried using likewise to establish this but it says:

--------------------------------------------------------------------------
The configuration stage 'open ports to DC' cannot be completed automatically. Please manually perform the following steps and rerun the domain join:

Some required ports on the domain controller could not be contacted. Please update your firewall settings to ensure that the following ports are open to '192.168.1.6':
	88  UDP
	389 UDP
	464 UDP
	123 UDP
	88 TCP
	389 TCP
	464 TCP

-------------------------------------------------------------------------
Configuration of server:


# Samba config file created using SWAT
# from UNKNOWN (&#152;·ô¿©·èã¹ÐŠ&#137;·ÈÃ¿W¡£·èã¹Ã§ü·äÃ¿)
# Date: 2009/02/09 03:53:44

[global]
	
	netbios name = VSERVER
	Workgroup = VDOMAIN
	server string = Voncloft  Server (Samba, XEBIAN (XBOX))
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
	logon path = \\vserver\profiles\%U
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
[all]
	path = /
	read only = no
	browseable = yes
	guest ok = Yes
[homes]
	comment = Home Directories
	path = /home/%u
	read only = No
	guest ok = Yes

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
	comment = Network Profiles Share
	path = /etc/samba/profiles
	read only = No
	create mask = 0600
	directory mask = 0700
	profile acls = Yes
	hide files = /desktop.ini/outlook*.lnk/*Briefcase*/
	store dos attributes = Yes
	browseable = No
	csc policy = no
	guest ok = Yes

--------------------------------------------------------------------------
Any help would greatly be appreciated.  If this were possible would I be able to switch between local and server like in windows or would it be strictly local or strictly network.

---

### Post by voncloft on 2009-11-21
Anybody? Beuler, Beuler, Beluer.....

---

