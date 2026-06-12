---
title: "Failed to retrieve share list from server"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by malfindin on 2009-12-15
I just installed GADMIN-SMABA on my Ubuntu 9.10 system and I now get the error "Failed to retrieve share list from server", when trying to browse my network. 

I have no Windows systems on the network and I don't need to connect to any EVER! Despite being a MCSE, Windows has blissfully been removed from my life.

The problem seems to only be on my 9.10 which I have tried to set up as a SAMBA server. It neither sees the network nor does the network see it. I can ping it though. If anyone has a quick fix for this I'd appreciate it. Help me Obi-wan you're my only hope.:)

Here's the output of testparm:

owner@Ubuntu-9:~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
WARNING: The "share modes" option is deprecated
Processing section "[netlogon]"
WARNING: The "share modes" option is deprecated
Processing section "[profiles]"
Processing section "[printers]"
WARNING: The "share modes" option is deprecated
Processing section "[pdf-documents]"
Processing section "[pdf-printer]"
Processing section "[Public]"
WARNING: The "share modes" option is deprecated
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_DOMAIN_PDC

Press enter to see a dump of your service definitions

[global]
	workgroup = IMF
	netbios name = SAMBA24
	server string = Samba file and print server
	interfaces = 127.0.0.1/8, 192.168.0.0/24
	bind interfaces only = Yes
	update encrypted = Yes
	client schannel = No
	server schannel = No
	allow trusted domains = No
	obey pam restrictions = Yes
	guest account = smbguest
	passwd program = /usr/bin/passwd '%u'
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	passwd chat timeout = 120
	username map = /etc/samba/smbusers
	password level = 6
	username level = 6
	unix password sync = Yes
	log file = /var/log/samba/samba.log
	max log size = 1000
	name resolve order = wins lmhosts bcast
	client signing = No
	client use spnego = No
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = cups
	machine password timeout = 120
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	delete user script = /usr/sbin/userdel '%u'
	add group script = /usr/sbin/groupadd '%g'
	delete group script = /usr/sbin/groupdel '%g'
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	logon script = %G.bat
	logon path = \\%L\profiles\%u
	logon drive = m:
	logon home = \\%L\homes\%u
	domain logons = Yes
	os level = 33
	preferred master = Yes
	dns proxy = No
	remote announce = 192.168.0.255
	remote browse sync = 192.168.0.255
	idmap uid = 16777216-33554431
	idmap gid = 16777216-33554431
	template shell = /dev/null
	winbind separator = @
	winbind cache time = 360
	winbind use default domain = Yes
	winbind trusted domains only = Yes
	winbind nested groups = No
	winbind nss info = no
	hosts allow = 127., 192.168.0.
	cups options = raw
	follow symlinks = No

[homes]
	comment = Home Directories
	path = /home
	guest ok = Yes
	locking = No

[netlogon]
	comment = Network Logon Service
	path = /home/netlogon
	guest ok = Yes
	locking = No

[profiles]
	comment = User Profiles
	path = /var/samba/profiles
	read only = No
	create mask = 0600
	directory mask = 0700
	browseable = No
	browsable = No
	locking = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	printable = Yes
	browseable = No
	browsable = No
	locking = No

[pdf-documents]
	comment = Converted PDF Documents
	path = /home/pdf-documents
	read only = No
	guest ok = Yes

[pdf-printer]
	comment = PDF Printer Service
	path = /tmp
	guest ok = Yes
	printable = Yes
	printing = bsd
	print command = /usr/bin/gadmin-samba-pdf %s %u
	lpq command = 
	use client driver = Yes

[Public]
	comment = Public Access
	path = /home/owner/Public
	valid users = owner
	admin users = owner
	guest ok = Yes
	locking = No
owner@Ubuntu-9:~$

---

