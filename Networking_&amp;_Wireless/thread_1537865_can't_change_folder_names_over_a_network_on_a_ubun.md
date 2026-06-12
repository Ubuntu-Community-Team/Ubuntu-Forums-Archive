---
title: "can't change folder names over a network on a ubuntu machine using a mac machine"
date: 2010-07-24
forum: Networking &amp; Wireless
---

### Post by pederjohn on 2010-07-24
heya

I am struggling with my mbp(macbook pro) at the moment,

It seems whenever i create a folder it creates the folder as untitled folder, but i can't change the folder name :mad: it just says "you don't have permission to rename item" but yet i created the folder and it is there.

One thing i have noticed is that once i enter a folder it won't even let me move the folder.

I hope someone can help 

Warm Regards
Peder

I am running Ubuntu 9.04

---

### Post by Morbius1 on 2010-07-24
You're the second person in as many days that seems to have this odd permissions problem from a Mac client. Please post the output of the following commands so we can see how your ubuntu machine is set up ( and I assumed you are using samba ):

```
net usershare info
``````
testparm -s
```

---

### Post by pederjohn on 2010-07-24
i don't get anything from the  "net usershare info"

but from testparm -s:

> 
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Drive1 200GB]"
Processing section "[Drive2 1TB]"
Processing section "[Drive3 50G]"
Processing section "[Drive4 80G]"
Processing section "[Drive5 250G]"
Processing section "[Drive6 120GB]"
Processing section "[ML-1610]"
WARNING: The "share modes" option is deprecated
Loaded services file OK.
Invalid combination of parameters for service ML-1610. 			   Level II oplocks can only be set if oplocks are also set.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	map to guest = Bad User
	obey pam restrictions = Yes
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

[Drive1 200GB]
	comment = 200GB
	path = media/Drive1
	read only = No
	guest ok = Yes

[Drive2 1TB]
	comment = 1TB
	path = media/Drive2
	force user = peder
	force group = peder
	read only = No
	guest ok = Yes

[Drive3 50G]
	comment = 50G
	path = media/Drive5
	read only = No
	guest ok = Yes

[Drive4 80G]
	comment = 80G
	path = media/Drive4
	read only = No
	guest ok = Yes

[Drive5 250G]
	comment = 250G
	path = media/Drive5
	read only = No
	guest ok = Yes

[Drive6 120GB]
	comment = 120GB
	path = media/Drive6
	read only = No
	guest ok = Yes

[ML-1610]
	comment = Samsung ML-1610
	path = /var/spool/samba
	read only = No
	create mask = 0700
	guest ok = Yes
	printable = Yes
	printer name = ML-1610
	oplocks = No
	share modes = No


---

### Post by Morbius1 on 2010-07-24
And what are the linux permissions on the target directories:

```
ls -al /media
```

---

### Post by pederjohn on 2010-07-24
total 68
drwxr-xr-x 10 root  root  4096 2010-04-10 17:02 .
drwxr-xr-x 21 root  root  4096 2010-05-25 20:10 ..
lrwxrwxrwx  1 root  root     6 2010-04-10 14:41 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2010-04-10 14:41 cdrom0
drwxrwxrwx  1 root  root 16384 2010-06-11 15:51 Drive1
drwxrwxrwx 24 peder root  4096 2010-07-24 16:47 Drive2
drwxr-xr-x  3 root  root  4096 2010-04-10 14:41 Drive3
drwxrwxrwx  1 root  root  4096 2010-04-06 22:51 Drive4
drwxrwxrwx  1 root  root 12288 2010-05-15 18:52 Drive5
drwxrwxrwx  1 root  root 12288 2010-07-22 17:36 Drive6
lrwxrwxrwx  1 root  root     7 2010-04-10 14:41 floppy -> floppy0
drwxr-xr-x  2 root  root  4096 2010-04-10 14:41 floppy0

---

### Post by Morbius1 on 2010-07-24
I can't find anything wrong with any of that. The only oddity is share level security in your smb.conf:
>  	security = SHARE
The default is "security = user" and share level security hasn't been used for a while. All of your shares allow guest access though so I don't think that would matter. 

Sorry, I'll have to explore this a little more. Maybe I'll find something on the apple forums about this.

---

### Post by Morbius1 on 2010-07-24
Well, I've gone to the apple forums and this may sound silly but do you have "Column View" selected when you try to rename the "New Folder"?

If you set it to "List View" can you now rename the folder?

---

