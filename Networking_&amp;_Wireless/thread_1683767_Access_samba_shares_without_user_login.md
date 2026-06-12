---
title: "Access samba shares without user login"
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by yedidel on 2011-02-08
Hello,

I have set samba shared folders on my ubuntu 10.04, which Windows users on my network use. The problem is, even that I leave the computer on, they cannot access the shared folders until I login with my account to the computer.
This is a real problem since I either need to come to the office, login with NX or tell them the password which I don't want to do.

Any way to run samba as a service even when no users are logged in?

---

### Post by Morbius1 on 2011-02-08
There are two ways to create Samba shares. One using nautilus and one using smb.conf. As it turns out both of these types of shares are accessible without anyone logging into the server so I'm at a loss about the nature of the problem.

I don't think there is anything in smb.conf that can turn this off but you might want to post the output of the following command to see if there's something odd in there:
```
testparm -s
```

---

### Post by yedidel on 2011-02-08
here is the output:


Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[sce]"
Processing section "[londonishi]"
Processing section "[credit]"
Processing section "[tecnosac]"
Processing section "[cvm]"
Processing section "[share]"
Processing section "[Documents]"
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
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[sce]
	path = /home/yedidel/public_html/sce
	valid users = dimitriy
	read only = No

---

### Post by cjhabs on 2011-02-08
Samba usually starts up during boot up - you should see Samba startup files in /etc/rc*.d which are links to /etc/init.d/samba

It sounds like the service is starting when you log in - I have not seen that before.

---

### Post by Morbius1 on 2011-02-08
This is a little beyond my experiences since the "servers" in my LAN are wired and the wireless devices are definitely clients.

Does the "server"  connect to the network wirelessly? Perhaps it's not that Samba isn't starting it's that the network isn't up until you login. 

Maybe something in here holds the answer: [http://ubuntuforums.org/showthread.php?t=1401075](http://ubuntuforums.org/showthread.php?t=1401075)

---

### Post by cjhabs on 2011-02-08
+1
You may need to switch from Network Manager to Wicd, which starts up the network at boot time.
You can check this by trying to "ping" the SAMBA server before you log in - if it responds then that isn't the issue.

---

