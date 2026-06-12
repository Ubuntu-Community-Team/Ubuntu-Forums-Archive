---
title: "Cannot unshare Personal Public Folder Ubuntu 10.04"
date: 2010-07-23
forum: Networking &amp; Wireless
---

### Post by glickboy on 2010-07-23
Hi everyone, Running ubuntu 10.04 I set up personal file sharing by going to System->Preferences->Personal File Sharing and clicking enable. I then installed Samba, and installed apache and dnssd.  I then right clicked on my folder i wanted to share selected Sharing Options and clicked share folder.  It worked beautifully and after a reboot could access the folder from my other machine.  Trouble started when i wanted to share another folder instead.  I right clicked on the folder, went to went to sharing options, unclicked share folder and then clicked modify share...The Folder is still accessable from the other machine.  I rebooted, then checked to make sure that the folder is still unshared, yet its still accessible on the other machine.  I have been hunting the forums and internet for a solution to this but come up empty handed.  When i type the command "net usershare info" nothing is listed. When i type "sudo net usershare info" nothing is listed.  /var/lib/samba/usershares is empty.  The output of "testparms-s" is ...

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
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

I am at a loss I dont know what else to do or what it could be.

---

### Post by Morbius1 on 2010-07-23
The "right click > sharing options" is called Nautilus-share and is part of Samba. "Personal File Sharing" uses a baby apache server and avahi to share only one folder: /home/your_user_name/Public. It does that automatically. It has nothing to do with Samba.

To "unshare" the "Public" folder you need to go back into System->Preferences->Personal File Sharing and disable it.

---

### Post by glickboy on 2010-07-24
Thanks Mobius1.  I was confused. I thought they were related :)

---

