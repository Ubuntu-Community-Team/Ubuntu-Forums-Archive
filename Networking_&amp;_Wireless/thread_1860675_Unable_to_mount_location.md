---
title: "Unable to mount location"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by peterbayliss81 on 2011-10-15
Hi,

I just updated to 11.10 and now i cant use my windows shares.

I have a Windows Home Server on my network and before the update i was able to see and use all the shares on this server perfectly. Now since the update, i can still see the server, but if i try to access it, i get the message

"Unable to mount location
Failed to retrieve share list from server"


Can anyone help me?

Thanks

---

### Post by woodhome on 2011-10-15
same problem here. Nothing fancy in the setup. Just an ordinary workgroup. Internet connection is obviously fine.

---

### Post by vector_force on 2011-10-15
Quick workaround for this bug follows:

sudo nautilus
then exit

launch nautilus regularly and you should be able to get in from now on

---

### Post by capscrew on 2011-10-15
> **peterbayliss81 said:**
> Hi,

I just updated to 11.10 and now i cant use my windows shares.

I have a Windows Home Server on my network and before the update i was able to see and use all the shares on this server perfectly. Now since the update, i can still see the server, but if i try to access it, i get the message

"Unable to mount location
Failed to retrieve share list from server"


Can anyone help me?

Thanks

From the terminal, post the output of```
testparm -s
```

And also the output of ```
hostname
```

@woodhome -- follow along, I think this will help you too.

---

### Post by peterbayliss81 on 2011-10-15
peter@peter-Inspiron-1525:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
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
peter@peter-Inspiron-1525:~$ hostname
peter-Inspiron-1525
peter@peter-Inspiron-1525:~$

---

### Post by capscrew on 2011-10-16
> **peterbayliss81 said:**
> ```
peter@peter-Inspiron-1525:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
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
```
```
peter@peter-Inspiron-1525:~$ hostname
peter-Inspiron-1525
peter@peter-Inspiron-1525:~$
```

The default install requires modification of the /etc/samba/smb.conf as shown below.  The one caveat is: When you substitute your machine's hostname for the NETBIOS name it should be less than 15 characters long.

For the hostname *peter-Inspiron-1525* you might use ***peter-Inspiron*** as the netbios name.

Add this to the [global] section

```
netbios name = <hostname>
name resolve order = bcast host

```
Then either restart the smbd and nmbd services or reboot the system.

You should now be able to browse the network shares.

---

