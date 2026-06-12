---
title: "Change in samba's handling of [home] shares in Karmic?"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by itFinallyWorks on 2009-11-11
Hello,
  I recently upgraded from jaunty to karmic.  On jaunty, I setup samba to have some shares usable and browseable by anonymous users.  I also had a [homes] section for home directories.  When asked to open one of these shares, windows would prompt for a password.

Now, however, on karmic when attempting to access one of the homes shares, windows simply gives an error about incorrect passwords.

I have tried experimenting with the security = parameter.  When security = share, the anonymous shares work fine, but the homes shares do not.   When security = user, the anonymous shares do not work, but the homes shares do.

The configuration should be exactly the same as on jaunty - I copied the smb.conf file (actually the entire /etc/samba contents) from the old installation and copied all the relevant users and groups over.

Any suggestions about where to look?

My smb.conf file:
```
[global]
	workgroup = HOME
	server string = Samba file and print server
	security = SHARE
	update encrypted = Yes
	guest account = smbguest
	pam password change = Yes
	passwd program = /usr/bin/passwd '%u'
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	passwd chat timeout = 120
	password level = 6
	username level = 6
	unix password sync = Yes
	log file = /var/log/samba/samba.log
	max log size = 1000
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	delete user script = /usr/sbin/userdel '%u'
	add group script = /usr/sbin/groupadd '%g'
	delete group script = /usr/sbin/groupdel '%g'
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	preferred master = Yes
	wins support = Yes
	winbind use default domain = Yes
	username = %S
	unix extensions = no

[homes]
	comment = Home Directories
	path = /home/%S
	read only = No
	browseable = No
	locking = No

[Public]
	path = /home/publicUser/Public
	guest ok = Yes

```

---

