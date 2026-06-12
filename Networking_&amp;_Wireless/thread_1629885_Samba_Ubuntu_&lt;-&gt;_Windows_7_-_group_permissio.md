---
title: "Samba Ubuntu &lt;-&gt; Windows 7 - group permissions not working on client side"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by Huib on 2010-11-24
I have an Ubuntu 10.10 server running, which serves as a PDC, on which a number of windows 7 clients log on.

I wanted to create a share on which users can create and delete files, but not edit them. So what I did was:
- adding the relevant users to a certain group ("commongroup")
- forcing ownership on all files and dirs on the share to commonuser.commongroup
- giving dirs on that share 775 permissions (making their content writable for members of the group)
- giving files 444 permissions (making them read-only)

All works fine when I test it with a ssh login on the server, but when I try to delete a file using Explorer on a windows client, I get the error: "the action can't be completed because the file is open in another program".

I took a look at the samba log for the relevant machine, but nothing was included for that error.

When I change the a file's permissions to 644, I can delete it from the windows side, but that will make it editable again, which I don't want.

So my question is: Is it possible to let all unix permissions work properly from the windows 7 clients?


My smb.conf as parsed by testparm (the specific share is called "resources"):

```

[global]
	workgroup = CLEVR
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
	unix extensions = No
	add machine script = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
	logon drive = H:
	domain logons = Yes
	os level = 64
	preferred master = Yes
	domain master = Yes
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	wide links = Yes

[homes]
	comment = Home Directories
	read only = No
	browseable = No

[netlogon]
	comment = Network Logon Service
	path = /var/samba/netlogon
	guest ok = Yes
	share modes = No

[profiles]
	comment = Users profiles
	path = /var/samba/profiles
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

[resources]
	comment = Resource Library
	path = /mnt/raid/resources
	force user = commonuser
	force group = commongroup
	read only = No
	create mask = 0444
	directory mask = 0775
	guest ok = Yes

[public]
	comment = Public Folder
	path = /mnt/raid/pub
	write list = huib, daniel, niels, guntur
	force user = commonuser
	force group = commongroup
	read only = No
	create mask = 0644
	guest ok = Yes

```

---

