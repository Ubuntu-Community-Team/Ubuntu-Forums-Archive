---
title: "share modes deprecated..why?"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by ultratek on 2010-01-16
```
razertek@razertek-desktop:~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[Pictures]"
Processing section "[netlogon]"
WARNING: The "share modes" option is deprecated
Processing section "[profiles]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_DOMAIN_PDC
Press enter to see a dump of your service definitions

[global]
	workgroup = LXHOME
	netbios name = RAZERTEK
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
	name resolve order = lmhosts wins bcast host
	printcap name = cups
	add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
	add group script = /usr/sbin/addgroup --force-badname %g
	add machine script = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
	logon drive = H:
	domain logons = Yes
	dns proxy = No
	wins support = Yes
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap uid = 10000-20000
	idmap gid = 10000-20000
	template shell = /bin/bash
	winbind enum users = Yes
	winbind enum groups = Yes

[homes]
	comment = Home Directories
	path = /home
	valid users = %S
	read only = No
	create mask = 0775
	directory mask = 0775

[Pictures]
	comment = Pictures
	path = /home/razertek/Pictures
	force user = razertek
	read only = No
	guest ok = Yes

[netlogon]
	comment = Network Logon Service
	path = /home/samba/netlogon
	guest ok = Yes
	share modes = No

[profiles]
	comment = Users profiles
	path = /home/samba/profiles
	create mask = 0600
	directory mask = 0700
	browseable = No
	browsable = No

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
	write list = root, @lpadmin
razertek@razertek-desktop:~$ 

```

---

### Post by Morbius1 on 2010-01-16
For security and windows compatibility reasons I suspect. Remember Samba wasn't created for us in our little home networks, it was meant to be used in an enterprise environment.

The funny thing is, share level security has been deprecated for about 4 years or so. If it's deprecated why is it still available? Another interesting tidbit is that it's still implemented in a lot of NAS devices and was the default in the last version of Xandros ( I've been told ).

---

### Post by bigboy16 on 2011-02-10
that's problem caused by your share setting at smb.conf file, 
what ubuntu version that you use? cause the setting are different on different ubuntu version.

---

