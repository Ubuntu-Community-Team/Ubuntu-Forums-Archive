---
title: "How to restore old samba username passwords after reinstalling UBUNTU"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by Guruprasad on 2009-10-14
Hi All

I am using samba for sharing file. There are some 50 users who access the files. Everyone have set there own password using SWAT.

Now my Ubuntu crashed and I am planning to reinstall Ubuntu. after I reinstall how can I get the list of users and password back to the newly installed Ubuntu?

---

### Post by swerdna on 2009-10-14
Bit of a long shot. How are passwrods stored? Look in the [global] stanza of smb.conf to find out. If you don't know, post the [global] stanza here.

---

### Post by Guruprasad on 2009-10-14
/var/lib/samba/passdb.tdb

---

### Post by Guruprasad on 2009-10-14
[global]
	server string = 
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	deadtime = 5
	dns proxy = No
	ldap ssl = no
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	create mask = 0777
	directory mask = 0777
	veto files = /*.exe/*.lsp/*.vbs/*.inf/*.htt/

---

### Post by swerdna on 2009-10-14
I'd be inclined to back up the directories /var/lib/samba and /etc/samba using the "sudo cp -a" command, which will preserve the ownership, timestamps and mode (-a = archive). Then reinstall. Then return contents of those two directories into place.

---

