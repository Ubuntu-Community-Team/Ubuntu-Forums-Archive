---
title: "Cant see files on other pc"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by dontgetshocked on 2009-12-20
Here is some info,hope it helps explain.I have both pc's shareing folders.Samba is configured using the configuration tool.
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.3     DAVID-LAPTOP   [ELLIOTT] [Unix] [Samba 3.4.0]
192.168.1.4     DAVID-DESKTOP  [	ELLIOTT       ]
192.168.1.4     DAVID-DESKTOP  [	ELLIOTT       ]
192.168.1.4     DAVID-DESKTOP  [	ELLIOTT       ]
192.168.1.4     DAVID-DESKTOP  [	ELLIOTT       ]
david@david-laptop:~$

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
david@david-laptop:~$ 
Clicking on the DAVID-DESKTOP icon produces this error;
Unable to mount location Failed to retrieve share list from  server
I can ping each pc from the other one.
david@david-laptop:~$ sudo testparm /etc/samba/smb.conf
[sudo] password for david: 
\Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Downloads]"
Processing section "[Public]"
Processing section "[Videos]"
Processing section "[Music]"
Processing section "[Pictures]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = ELLIOTT
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	browseable = No
	browsable = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Downloads]
	comment = Netbook Downloads
	path = /home/david/Downloads
	read only = No
	guest ok = Yes

[Public]
	comment = Netbook Public
	path = /home/david/Public
	read only = No
	guest ok = Yes

[Videos]
	comment = Netbook Videos
	path = /home/david/Videos
	read only = No
	guest ok = Yes

[Music]
	comment = Netbook Music
	path = /home/david/Music
	read only = No
	guest ok = Yes

[Pictures]
	path = /home/david/Pictures
david@david-laptop:~$ ^C
david@david-laptop:~$ ^C
david@david-laptop:~$

---

