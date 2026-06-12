---
title: "Samba error for same named users"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by Fishbowler on 2009-08-11
A new problem has arisen on my Xubuntu box, which I can only assume has come from a recent binary or configuration change.

For the last few days, when attempting to browse from the Windows box to the Xubuntu box, I have been receiving:


[I]\\servername is not accessible. You might not have permission to use this network resource.
Contact the administrator of this server to find out if you have access permissions.

The account is not authorized to log in from this station.[/I]

I have the same username on both my windows 7 & Xubuntu box.

Since I know there have been a couple of recent updates to samba, my smb.conf is thus:

```

[global]
	workgroup = HERE
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	guest account = dan
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[FileShare]
	path = /media/DATA1/FileShare
	guest ok = Yes

[Uploads]
	path = /media/DATA1/Uploads
	read only = No
	guest ok = Yes

[EXTERNAL_HD]
	path = /media/EXTERNAL_HD
	read only = No
	guest ok = Yes

[Backups]
	path = /media/DATA4/Backups
	read only = No
	guest ok = Yes

```

I've recently regenerated it from its previous form using testparm in an attempt to address this issue.

I've used laptops to connect to shares on the box recently too (although I can't be certain that's after the recent issue arose). My XBMC'd Xbox can still access FileShare perfectly.

Attempting to map a network drive from Windows using alternate credentials "guest/<blank>" failed.

I've looked through the samba guide [here]("http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/") and found nothing applicable yet, although it's a might large document. Searching this forum hasn't yielded me anything either (other than the link to samba!).

Other than changing the username on one of the two machines, can anyone suggest anything?

---

### Post by swerdna on 2009-08-11
Try putting these lines into the [global] stanza:
```
local master = yes
preferred master = yes
name resolve order = bcast host lmhosts wins
os level = 33
```
Then check if the firewall is open for Samba with this command:
```
sudo ufw status
```If it returns statements about allowing samba, well and good. If not, then turn it off for the time being as a diagnostic test.

See here for more details: [The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

---

