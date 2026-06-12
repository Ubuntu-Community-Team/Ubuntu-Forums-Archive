---
title: "Samba will not install"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by DarthBalls on 2010-04-04
After upgrading to 9.10 when ever a samba dependent upgrade is attempted through the update manager the process hangs up at "configuring samba".I REMOVED samba, samba-common, winbind, etc.I tried-
 
$ sudo apt-get purge samba
$ sudo dpkg --configure -a
$ sudo apt-get install -f
$ sudo apt-get update && sudo apt-get upgrade
$ sudo apt-get install samba

and after that: the install simply hangs! 

steve@Burninator:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  samba-common samba-common-bin
Suggested packages:
  openbsd-inetd inet-superserver smbldap-tools ldb-tools
The following NEW packages will be installed:
  samba samba-common samba-common-bin
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/12.4MB of archives.
After this operation, 33.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package samba-common.
(Reading database ... 305558 files and directories currently installed.)
Unpacking samba-common (from .../samba-common_2%3a3.4.0-3ubuntu5.6_all.deb) ...
Selecting previously deselected package samba.
Unpacking samba (from .../samba_2%3a3.4.0-3ubuntu5.6_amd64.deb) ...
Selecting previously deselected package samba-common-bin.
Unpacking samba-common-bin (from .../samba-common-bin_2%3a3.4.0-3ubuntu5.6_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Processing triggers for ureadahead ...
Setting up samba-common (2:3.4.0-3ubuntu5.6) ...

Creating config file /etc/samba/smb.conf with new version

Setting up samba (2:3.4.0-3ubuntu5.6) ...
update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode.
Generating /etc/default/samba...
tdbsam_open: Converting version 0.0 database to version 4.0.
tdbsam_convert_backup: updated /var/lib/samba/passdb.tdb file.
account_policy_get: tdb_fetch_uint32 failed for field 1 (min password length), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 2 (password history), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 3 (user must logon to change password), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 4 (maximum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 5 (minimum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 6 (lockout duration), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 7 (reset count minutes), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 8 (bad lockout attempt), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 9 (disconnect time), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 10 (refuse machine password change), returning 0
Importing account for nobody...ok
Importing account for steve...ok
Importing account for smbguest...ok
Importing account for Vista-Machine$...ok
Importing account for squid...ok
Importing account for OldmanRiver$...ok
Importing account for Toshi$...ok

WTF!? Ubuntu x64 amd phenom quad core

---

### Post by alexdelprogramador on 2010-04-04
the best way to install samba, is to use synaptic, because it will istall all dependencies automaticaly.

so, start synaptic and then, find samba in the text box finder.

Im sure it will install it without troubles. ;)

---

### Post by DarthBalls on 2010-04-04
It's the same there- it just gets stuck-I've resolved all dependencies; no sharing for me. when I run gksu nautilus and right-click to share I get this

Nautilus-Share-Message: Called "net usershare add" but it failed: 'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Memory allocation error.

I've installed a new smb.conf and kept it simple. Still no sharing for me.Note I wrote a new smb.conf AFTER all this crap. I used the default and only added share definitions here's my testparm: 

steve@Burninator:~$ sudo testparm /etc/samba/smb.conf
[sudo] password for steve: 
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Public]"
Processing section "[Skool]"
Processing section "[Documents]"
Processing section "[Music]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = SMOKEMYGRUNDLE
	server string = burninator
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
	create mask = 0775
	directory mask = 0775

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

[Public]
	path = /home/steve/Public
	read only = No

[Skool]
	path = /home/steve/Skool
	read only = No

[Documents]
	path = /home/steve/Documents
        read only = yes  

[Music]
	path = /home/steve/Music
        read only = yes

---

