---
title: "Printer sharing issue"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by cscj01 on 2009-08-25
I am trying to share a Ubuntu printer with my home network that has XP PC's attached.  I have installed Samba and made the printer shareable, but I cannot see the printer from XP when I browse to add it.  When I type http://<Ubuntu PC name>:631/printers/<printer name> for the printer name on the XP Add printer dialog, I get a message saying that the server does not accept remote connections.  I have checked "Publish shared printers connected to this system" and "Allow printing from the Internet" on the Settings menu under System/Administration/Printing.  I used testparm to check out my Samba configuration.  It is as follows:

Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = HOME
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	printcap name = cups
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	path = /tmp
	create mask = 0700
	guest only = Yes
	guest ok = Yes
	printable = Yes
	use client driver = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

This is my first attempt at this, and I am a complete novice as far as Samba is concerned.  BTW, I can print to the printer with no problem under Ubuntu.  I do not know what all the settings are for in Samba (they are mostly defaults).  The parts I changed according to info at the Ubuntu forums discussions for setting up print sharing are the workgroup name and the [printers] section.

I am running Ubuntu 9.04 and XP SP3.  Any and all help is appreciated.

---

### Post by dmizer on 2009-08-25
Why not just use CUPS to share the printer with Windows?

System > administration > printing

Rather than using the Ubuntu PC name, try using the Ubuntu computer's IP address. If you don't know what the IP address is, you can find it by running this command:
```
ifconfig
```

---

### Post by cscj01 on 2009-08-25
Thank you very much.  I was able to browse to the cups printers page and add the printer using the ip address.  The reason I installed Samba was the documentation I read on the forums all said you needed to install it.  I am glad to know you don't need Samba to share a printer.

One question:  Why does the ip address work and the server name not work?  I'm learning as I go.

---

### Post by dmizer on 2009-08-25
> **cscj01 said:**
> One question:  Why does the ip address work and the server name not work?  I'm learning as I go.
While you don't need Samba to share a printer on the network, you do need Samba to allow Windows computers to view Ubuntu's name on the network.

A very simple smb.conf file can accomplish this:
```
[global]
workgroup = HOME
netbios name = [COLOR="Red"]ubuntu-name[/COLOR]
server string = %h server (Samba, Ubuntu)
```

Change [COLOR="Red"]ubuntu-name[/COLOR] to your actual Ubuntu computer's name. Also, make sure that the Windows work group is actually "HOME".

That, or you need a local DNS server.

---

### Post by Dragonflyoh on 2009-08-27
I am experiencing the same problems with a printer shared on my Ubuntu system. I tried all of the suggested remedies and I still get a note on my windows PC that access to the printer is denied. Below is the result of testparm. I also can print with no problems from the Ubuntu PC. Every now and then after changing settings I get a note under policies that says the printer is "not published see server settings". I check the server settings, change nothing, come back and the message is gone. Any ideas would be appreciated.

Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
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

---

