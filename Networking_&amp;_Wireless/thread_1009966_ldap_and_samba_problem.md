---
title: "ldap and samba problem"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by ChristofLaeremans on 2008-12-13
Hello, 

I'm trying to create a network at our school. I've installed the samba server and configured it as an PDC. The openLDAP server is also installed and I can browse the users that I created with the LDAP Account Manager (LAM). The installation guide that u use to setup and configure the samba and LDAP server is : [https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html](https://help.ubuntu.com/8.10/serverguide/C/samba-ldap.html)

But the problem is that only the users created by the installation of ubuntu 8.10 (server version) has the possibility to connect to the ABULEDU domain. Al the other users created by LAM of with the smbldap-useradd command can't logon. 

Can someone help me ? I also post my smb.conf file (maybe there is an error in this file) 

--BEGIN--
[global]
	workgroup = ABULEDU
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = ldapsam:ldap://localhost/
	pam password change = Yes
	passwd program = /usr/sbin/smbldap-passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	unix extensions = No
	add user script = /usr/sbin/smbldap-useradd -m "%u"
	delete user script = /usr/sbin/smbldap-userdel "%u"
	add group script = /usr/sbin/smbldap-groupadd -p "%g"
	delete group script = /usr/sbin/smbldap-groupdel "%g"
	add user to group script = /usr/sbin/smbldap-groupmod -m "%u" "%g"
	delete user from group script = /usr/sbin/smbldap-groupmod -x "%u" "%g"
	set primary group script = /usr/sbin/smbldap-usermod -g "%g" "%u"
	add machine script = /usr/sbin/smbldap-useradd -w "%u"
	logon drive = H
	domain logons = Yes
	os level = 255
	preferred master = Yes
	domain master = Yes
	dns proxy = No
	ldap admin dn = cn=admin,dc=sacrecoeurcharleroi,dc=be
	ldap delete dn = Yes
	ldap group suffix = ou=Groups
	ldap idmap suffix = ou=Idmap
	ldap machine suffix = ou=Computers
	ldap passwd sync = Yes
	ldap suffix = dc=sacrecoeurcharleroi,dc=be
	ldap ssl = no
	ldap user suffix = ou=People
	panic action = /usr/share/samba/panic-action %d
	admin users = root

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[homes]
	comment = Home map gebruikers
	path = /home
	valid users = %S
	read only = No

[netlogon]
	comment = netlogon service
	path = /home/samba/netlogon/%g
	browseable = No
	available = No

[profiles]
	comment = Windows Zwervende profielen
	path = /home/samba/profielen
	valid users = %U
	read only = No
	create mask = 0600
	directory mask = 0700
	profile acls = Yes
	browseable = No
	available = No
--END--

Thanks, 

Christof Laeremans
Teacher @ Collège du Sacré-Coeur Charleoi (Belgium)

---

