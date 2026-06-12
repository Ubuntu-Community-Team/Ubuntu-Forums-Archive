---
title: "Network backup"
date: 2011-01-27
forum: Networking &amp; Wireless
---

### Post by aeh on 2011-01-27
I have two desktop machines, each with U 10.10. I want to backup data on my main machine to a partition on the other machine. I am going to use luckybackup for that. Problem is, from the main machine, I cannot access the backup partition on the other machine (but I can see it). I get prompts for passwords and when I enter them nothing happens, it seems they're not valid. Bottom line, I can't access that partition. Any ideas?

A

---

### Post by Grenage on 2011-01-27
Are the credentials for both machines the same?
If not, are you using credentials for the remote machine?
How are you sharing the partition?
How are you accessing the partition?

---

### Post by aeh on 2011-01-27
> **Grenage said:**
> Are the credentials for both machines the same?
If not, are you using credentials for the remote machine?
How are you sharing the partition?
How are you accessing the partition?



Credentials? Same passwords and all that. Permissions and ownership, I hope so, I sure have tried to make myself the owner of relevant folders

Sharing the partition? The normal way I guess (I am a newbie shen it comes to networking)
How am I accessing the partition? It is an otherwise unused partition that I mount separately (sda3)

---

### Post by Grenage on 2011-01-27
Ok, so it's the same user/pass on both machines; it shouldn't matter, it just clears that up.

I presume that you are accessing the share through the usual file manager (nautilus).  Did you create the share using nautilus on the other machine?

---

### Post by Morbius1 on 2011-01-27
Why not post the output of the following commands so we can deal with facts please:

From the machine you want to backup to:
```
testparm -s
``````
net usershare info --long
```

---

### Post by aeh on 2011-01-28
Here:

aeh@ubu:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[aeh]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	map to guest = Bad User
	obey pam restrictions = Yes
	guest account = aeh
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d
	guest ok = Yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[aeh]
	path = /home/aeh
	valid users = aeh, nobody
	read only = No







aeh@ubu:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[aeh]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	map to guest = Bad User
	obey pam restrictions = Yes
	guest account = aeh
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d
	guest ok = Yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[aeh]
	path = /home/aeh
	valid users = aeh, nobody
	read only = No

---

### Post by aeh on 2011-01-28
I screwed up
here's the rest:

aeh@ubu:~$ net usershare  info --long
info_fn: file /var/lib/samba/usershares/backup-ubu is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[media-ubu]
path=/media
comment=
usershare_acl=Everyone:R,UBU\aeh:F,
guest_ok=n

[backup sda3]
path=/media/sda3
comment=
usershare_acl=Everyone:R,UBU\aeh:F,
guest_ok=n

aeh@ubu:~$

---

### Post by Morbius1 on 2011-01-28
I'm going to focus on the Nautilus-share because your smb.conf is a little too odd for me:
> [backup sda3]
path=/media/sda3
comment=
usershare_acl=Everyone:R,UBU\aeh:F,
[COLOR=Blue]guest_ok=n[/COLOR]You've got quest access disabled so you're going to have to create local users on the server and give them samba passwords. If you want to access the share using your own server username then you will have to add it to the samba database:
```
sudo smbpasswd -a aeh
```

---

