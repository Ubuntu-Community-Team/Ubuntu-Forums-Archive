---
title: "need help with sharing files"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by Irti on 2010-03-03
i am tying to share some file with my friends over the network..so i go to the network folder but and i see my friend's pc...but i can't access it...so i right click on the folder i want to share and set it as shared....and i ask my friend to try and access it ..well... it doesnt work...then i try sudo nautilus ..go to the properties and try to change permissions and whenever i try to change it..it just keeps coming back to my name..it doesnt allow me to change the permissions either...can someone plss throw some light on what exactly is the problem over here and how do i got about solving it..getting a bit frustrated now!!!

---

### Post by Morbius1 on 2010-03-03
Without any detail it sounds like a linux permissions problem not a samba access problem. Post the output of the following commands so we can see how everything is configured:

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**
Type **testparm -s**

There is one more command. It will tell us the permissions on the folder you are trying to share:

**ls -dl /path_to_shared_folder**

So if you're sharing /media/xyz then the command would be:

**ls -dl /media/xyz**

---

### Post by Irti on 2010-03-09
sorry for the delayed reply... I was very busy the past few days and didnt have the time to follow this up...well here are the details from the commands

this was from testparm -s

Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
WARNING: The "share modes" option is deprecated
Processing section "[netlogon]"
WARNING: The "share modes" option is deprecated
Processing section "[profiles]"
Processing section "[printers]"
WARNING: The "share modes" option is deprecated
Processing section "[pdf-documents]"
Processing section "[pdf-printer]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
	netbios name = SAMBA24
	server string = Samba file and print server
	interfaces = 127.0.0.1/8, 192.168.0.0/24
	bind interfaces only = Yes
	update encrypted = Yes
	client schannel = No
	server schannel = No
	allow trusted domains = No
	obey pam restrictions = Yes
	guest account = smbguest
	passwd program = /usr/bin/passwd '%u'
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	passwd chat timeout = 120
	username map = /etc/samba/smbusers
	password level = 6
	username level = 6
	unix password sync = Yes
	log file = /var/log/samba/samba.log
	max log size = 1000
	name resolve order = wins lmhosts bcast
	client signing = No
	client use spnego = No
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = cups
	machine password timeout = 120
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	delete user script = /usr/sbin/userdel '%u'
	add group script = /usr/sbin/groupadd '%g'
	delete group script = /usr/sbin/groupdel '%g'
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	logon script = %G.bat
	logon path = \\%L\profiles\%u
	logon drive = m:
	logon home = \\%L\homes\%u
	os level = 33
	local master = No
	domain master = No
	dns proxy = No
	remote announce = 192.168.0.255
	remote browse sync = 192.168.0.255
	idmap uid = 16777216-33554431
	idmap gid = 16777216-33554431
	template shell = /dev/null
	winbind separator = @
	winbind cache time = 360
	winbind use default domain = Yes
	winbind trusted domains only = Yes
	winbind nested groups = No
	winbind nss info = no
	hosts allow = 127., 192.168.0.
	cups options = raw
	follow symlinks = No

[homes]
	comment = Home Directories
	path = /home
	read only = No
	locking = No
	share modes = No

[netlogon]
	comment = Network Logon Service
	path = /home/netlogon
	locking = No
	share modes = No

[profiles]
	comment = User Profiles
	path = /var/samba/profiles
	read only = No
	create mask = 0600
	directory mask = 0700
	browseable = No
	browsable = No
	locking = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	printable = Yes
	browseable = No
	browsable = No
	locking = No
	share modes = No

[pdf-documents]
	comment = Converted PDF Documents
	path = /home/pdf-documents
	read only = No
	guest ok = Yes

[pdf-printer]
	comment = PDF Printer Service
	path = /tmp
	guest ok = Yes
	printable = Yes
	printing = bsd
	print command = /usr/bin/gadmin-samba-pdf %s %u
	lpq command = 
	use client driver = Yes

this is from ls -dl

irteza@ICTCTRGF:~$ ls -dl /home/irteza/Public/
drwxrwxrwx 2 irteza irteza 4096 2010-02-21 15:51 /home/irteza/Public/

thanx for helping me out

---

### Post by Morbius1 on 2010-03-09
That smb.conf file is insane and I'm guessing is the result of using gadmin or some other samba utility. Maybe someone else will be willing to spend the next two weeks to try and fix all that but for my money I would start over again. This is what I personally would do if it was my system:

First: Make sure that on your system the following file actually exists:
/usr/share/samba/smb.conf
If it does then follow these steps:

Open **Terminal**
Type **sudo cp /etc/samba/smb.conf /etc/samba/smb.confORIG**
[COLOR=Blue]*This will create a copy of the current smb.conf and call it smb.confORIG*[/COLOR]
Type **sudo cp -a /usr/share/samba/smb.conf /etc/samba/**
[COLOR=Blue]*This will copy the originally installed smb.conf in /usr/share/samba to /etc/samba.*[/COLOR]

Now that you're back to a "factory fresh" state you should make the following modifications to smb.conf"

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Add the following lines to the [COLOR=Blue][global][/COLOR] section of smb.conf:
```
netbios name = SAMBA24
force user = irteza
```Save the file, exit gedit, and back in the terminal type: [B]sudo service samba restart
[/B]
Now go into Nautilus, right click on **/home/irteza/Public/** and select "Sharing Options". Mark all the boxes and select "Create Share".

Now see if the other box can access the share.

---

### Post by Irti on 2010-03-13
thanks...will try it out...too lazy..hehe...guess i could just use a usb

---

