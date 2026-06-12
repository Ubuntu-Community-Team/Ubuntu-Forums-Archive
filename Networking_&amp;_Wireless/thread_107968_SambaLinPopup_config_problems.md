---
title: "Samba/LinPopup config problems"
date: 2005-12-24
forum: Networking &amp; Wireless
---

### Post by jet87 on 2005-12-24
Hi all.

I installed Ubuntu a week ago and have been enjoying Linux greatly.  I was happy when I could use Smb4k to browse the Windows workgroup my home is on.  I had tried some other distributions before, and it was hit or miss.  One of the things I've been working on getting to work is LinPopup, and have had no success.

A few days ago (around when I installed kubuntu-desktop, but I don't think these are related),  Smb4k stopped seeing the other computers on the network.  I can't access the computers through Konqueror either.  LinPopup still doesn't work.  I've tried searching Google, samba.org, and Ubuntu forums, but have not come across any solutions.  Hopefully I can find some help here.  For your convenience, here is my smb.conf file.

```
[global]
	log file = /var/log/samba/log.%m
	load printers = yes
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n
	socket options = TCP_NODELAY
	obey pam restrictions = yes
	passdb backend = tdbsam guest
	passwd program = /usr/bin/passwd %u
	wins support = true
	dns proxy = no
	netbios name = LINUX
	netbios aliases = tim
	printing = cups
	server string = %h server (Samba, Ubuntu)
	invalid users = root
;linpopup-removed 	message command = /bin/sh -c '/usr/bin/linpopup 
	workgroup = JARZ9999
	os level = 20
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000

[homes]
   comment = Home Directories
   browseable = yes
   writable = yes
   create mask = 0755
   directory mask = 0755

;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[printers]
   comment = All Printers
   browseable = yes
   path = /tmp
   printable = yes
   public = yes
   writable = no
   create mode = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes

;   write list = root, @ntadmin


[SharedDocs]
path = /home/jet87/shared
comment = Linux
available = yes
browseable = yes
public = yes
writable = yes
```

Thanks in advance for any help.

Tim J.

---

