---
title: "Sharing External HDD on Ubuntu Desktop Cpu with Windows 7 Cpu"
date: 2012-12-04
forum: Networking &amp; Wireless
---

### Post by Terryfab24 on 2012-12-04
So I have researched information on sharing my external harddrive which is attached to my desktop cpu running ubuntu 12.04 and having it accessible with my windows 7 cpu. Most people have suggested doing the method of gksu gedit /etc/sambu/smb.conf by adding force user = my username under global in the smb.conf file or adding it to area that mentions the share itself (see below).

ExternalHDD]
	path = /media/ExternalHDD
	available = yes
;	browsable = yes
	public = yes
	writable = yes
	force User = terry

After making the edit I run sudo service smbd restart.  However, no matter what edit I perform, I still can't access the particular share from my windows cpu.  I see the shared folder but can't access it, saying I do not have permission to do so.  I have no problem accessing all my other shares music, videos etc. Is there something I am missing or not doing correctly.  Please let me know.  I am willing to set up the share all over again it need be. Let me know if you need anything from me.

Thanks for your help in advance...

---

### Post by Morbius1 on 2012-12-05
There are 2 ways to create a Samba share. One is through Nautilus and the other is to add a share definition in smb.conf. That's why there are 2 recommendations to where to put the "force user" option. If you have used both methods they may be in conflict. Post the output of the following commands to see what method you are using and how you are using it:
```
testparm -s
net usershare info --long
```Might as well post the output of this one so we know how it's mounting:
```
ls -dl /media/ExternalHD
```

---

### Post by Terryfab24 on 2012-12-05
terry@ubuntudesktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Music]"
Processing section "[Videos]"
Processing section "[Documents]"
Processing section "[Pictures]"
Processing section "[Downloads]"
Processing section "[ExternalHDD]"
Processing section "[DesktopBackup]"
WARNING: The security=share option is deprecated
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	map to guest = Bad User
	obey pam restrictions = Yes
	guest account = terry
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
	idmap config * : backend = tdb
	guest ok = Yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	read only = No

[Music]
	path = /home/terry/Music
	read only = No

[Videos]
	path = /home/terry/Videos
	read only = No

[Documents]
	path = /home/terry/Documents
	read only = No

[Pictures]
	path = /home/terry/Pictures
	read only = No

[Downloads]
	path = /home/terry/Downloads
	read only = No

[ExternalHDD]
	path = /media/ExternalHDD
	force user = terry
	read only = No

[DesktopBackup]
	path = /media/DesktopBackup
	force user = terry
	read only = No
terry@ubuntudesktop:~$ net usershare info --long

---

### Post by Terryfab24 on 2012-12-05
terry@ubuntudesktop:~$ ls -dl /media/ExternalHDD
drwx------ 1 terry terry 4096 Dec  3 22:10 /media/ExternalHDD

---

### Post by Terryfab24 on 2012-12-06
Posted what you asked...let me know what you want me to do next

> **Morbius1 said:**
> There are 2 ways to create a Samba share. One is through Nautilus and the other is to add a share definition in smb.conf. That's why there are 2 recommendations to where to put the "force user" option. If you have used both methods they may be in conflict. Post the output of the following commands to see what method you are using and how you are using it:
```
testparm -s
net usershare info --long
```Might as well post the output of this one so we know how it's mounting:
```
ls -dl /media/ExternalHD
```

---

### Post by Terryfab24 on 2012-12-13
Do I have this posted in the wrong area? No one has responded...

---

