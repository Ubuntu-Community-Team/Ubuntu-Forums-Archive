---
title: "Samba transfer bandwidth"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by inobe on 2009-11-26
hi i have ubuntu 9.10

samba file transfer is poor averages around 150 kbps, i set up samba and the shares via terminal.

here is my testparm

```
testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[shares]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

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
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[shares]
	path = /home/bob/shares
	valid users = bob
	read only = No
	guest ok = Yes


```


if it helps i setup samba using these steps

```
sudo apt-get install samba
```

```
sudo smbpasswd -a username
```

```
mkdir /home/username/shares
```

backup smb
```
sudo cp /etc/samba/smb.conf ~
```

```
sudo gedit /etc/samba/smb.conf
```

added these to the end of smb.conf
```
[shares]
path = /home/username/shares
available = yes
valid users = username
read only = no
browsable = yes
public = yes
writable = yes
```

restarted samba
```
sudo /etc/init.d/samba restart
```

and ran 
```
testparm
```

i have the same problem on a kubuntu 9.10 machine, when i had 9.04 on these machines bandwidth averaged around 2500 kbps.

thanks for the assistance:)

---

### Post by inobe on 2009-11-26
[IMG]http://img510.imageshack.us/img510/9700/smbz.jpg[/IMG]

hey guys here is a image, thanks :)

---

### Post by inobe on 2009-11-27
i don't mean to "bump" this thread but so far i tried several things, maybe someone will see this that experienced similar issues could offer any tips ?


thanks :)

---

### Post by mhbell on 2009-11-30
> **inobe said:**
> i don't mean to "bump" this thread but so far i tried several things, maybe someone will see this that experienced similar issues could offer any tips ?


thanks :)

I am sorry that I can't help you. I have the same problem as well as some others in Ubuntu 9.10  I am about ready to go back to 9.04
Mel

---

