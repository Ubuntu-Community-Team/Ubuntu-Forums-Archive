---
title: "samba woes"
date: 2011-01-07
forum: Networking &amp; Wireless
---

### Post by mistafeesh on 2011-01-07
Hi,
I'm having trouble getting to my samba shares, and I'd appreciate some help.

I've tried accessing them with my username and password, sambaguest and computername\username and password.

Originally it was working with computername\username and password but I wanted to get it set not to have to include the computer name because my wii homebrew has to access it and they didn't think to include a backslash in the keyboard for the wii media player I use!

Now, however I cannot access it at all...I just get a user/pass failiure

Here's the result from running testparm -sp (as I saw from another post of a similar nature)


Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[www]"
Processing section "[work]"
Processing section "[stuff]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
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
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[www]
	path = /var/www
	valid users = %S
	read only = No
	create mask = 0775
	directory mask = 0775

[work]
	path = /home/dan/Documents
	valid users = %S
	read only = No
	create mask = 0775
	directory mask = 0775

[stuff]
	path = /media/STUFF
	valid users = %S
	read only = No
	create mask = 0775
	directory mask = 0775

---

### Post by luvshines on 2011-01-07
The entry 'valid users = %S' looks weird to me.

I tried it on my machine, couldn't seem to get it working.

Two questions:
1. What are you using it for ?
2. Can you try removing that, restarting the service and then give it a try ?

---

### Post by mistafeesh on 2011-01-09
oops double posted please ignore!

---

### Post by mistafeesh on 2011-01-09
I forgot I'd put that in(just trying different things from the various commented out stuff) but I've removed it and it's still the same...

I'm using this to share general files with 2 windows  laptops (vista and no.7) occasionally but mostly to share video files with a wii running wiiMC (a simple media centre ~ video and music player on the homebrew channel if that makes sense to anyone)

---

### Post by mistafeesh on 2011-01-10
Right, I've got it sorted now. I copied a fresh smb.conf over the top of that one and changed stuff around and it all works fine now... 
I'm not quite sure what I was doing wrong that I've now done right, but in case it's useful, here's my new settings:


Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[profiles]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[www]"
Processing section "[work]"
Processing section "[stuff]"
Loaded services file OK.
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

[homes]
	comment = Home Directories
	read only = No
	create mask = 0775
	directory mask = 0775

[profiles]
	comment = Users profiles
	path = /home/samba/profiles
	create mask = 0755
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

[www]
	comment = web server root
	path = /var/www
	read only = No
	guest ok = Yes

[work]
	path = /home/dan/Documents
	read only = No
	guest ok = Yes

[stuff]
	path = /media/STUFF
	read only = No
	guest ok = Yes

---

### Post by mistafeesh on 2011-01-10
dangnabbit! I had to restart the server earlier and now things have gone back to not working... I can't see anything that would/could make a difference to this - I've changed nothing...

any ideas? I still get a username/password error when I try to log on to the SMB server. I've got afp and nfs shares working fine for my mac and ubuntu laptop (which is also the vista laptop) fine but I just can't get my head around smb.conf

---

### Post by Kreacher on 2011-01-10
Please mark me as one of little knowledge. However, I had a few rounds getting my Ubuntu box to talk to my Windows boxes via my network. 

In smb.conf located in /etc/samba

workgroup = your-workgroup
name resolve order = lmhosts wins bcast host

Remove the semi-colon from the start of any line.

In nsswitch.conf ocated in /etc 

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

Note the order of the items and the additions. 

My testparm -sp results:

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = NCC-1701
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
    name resolve order = lmhosts wins bcast host
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

Good luck!

---

### Post by tosk on 2011-01-10
Your security type should be set to user and not share.

```
security = user
```

This will allow you to access the share using your Linux username/password.

---

### Post by mistafeesh on 2011-01-12
ah yes, I've changed that and now I can log in using username= servername\username and password=password

Is there a way I can get rid of having to add the server name and backslash to the username? I wouldn't mind but my wii doesn't have a backslash in the on screen keyboard!


EDIT - I'm going to mark this thread as solved and start another as this is a separate issue really. 

Thanks for your help everybody! I'm trying to move towards using open source in everything I do as well as trying to 'convert' my friends. This forum makes that a lot more possible!

---

