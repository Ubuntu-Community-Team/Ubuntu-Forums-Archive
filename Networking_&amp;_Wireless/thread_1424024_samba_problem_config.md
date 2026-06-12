---
title: "samba problem config"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by macstl on 2010-03-07
I got 9.10 on by laptop and xp on other computer. Installed samba server and xp recognized my laptop but not anything I share on ubuntu. am i missing something in samba config file? Im trying to share home directory on ubuntu and both systems have the same login id.:p

---

### Post by Morbius1 on 2010-03-07
There are two methods of sharing folders in ubuntu with configurations defined in two different locations. Please post the output of the following commands:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**

These will tell us what method you're using and how your shares are set up.

---

### Post by macstl on 2010-03-07
macstl@macstl-laptop:~$ net usershare info
[documents]
path=/home/macstl/Documents
comment=
usershare_acl=Everyone:R,
guest_ok=n

[pictures]
path=/home/macstl/Pictures
comment=
usershare_acl=Everyone:R,
guest_ok=n

[joemc]
path=/home/macstl/joemc
comment=
usershare_acl=Everyone:F,
guest_ok=n

[downloads]
path=/home/macstl/Downloads
comment=
usershare_acl=Everyone:R,
guest_ok=n

macstl@macstl-laptop:~$ b
b: command not found
macstl@macstl-laptop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
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
	name resolve order = lmhosts host wins bcast
	dns proxy = No
	wins support = Yes
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	comment = Users profiles
	path = /home/samba/profiles
	create mask = 0600
	directory mask = 0700
	browseable = No
	browsable = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	browseable = Yes
	browsable = Yes
macstl@macstl-laptop:~$ ^C
macstl@macstl-laptop:~$ ^C
macstl@macstl-laptop:~$ nano
macstl@macstl-laptop:~$ nano
macstl@macstl-laptop:~$ clear

macstl@macstl-laptop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
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
	name resolve order = lmhosts host wins bcast
	dns proxy = No
	wins support = Yes
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	comment = Users profiles
	path = /home/samba/profiles
	create mask = 0600
	directory mask = 0700
	browseable = No
	browsable = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	browseable = Yes
	browsable = Yes
macstl@macstl-laptop:~$ 

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

usershare info

path=/home/macstl/Documents
comment=
usershare acl=Everyone:R
guest_ok=n

---

### Post by Morbius1 on 2010-03-08
There are two issues here:

(1) Nautilus-share

You seem to be using Nautilus-share ( Right click > Sharing Options ) on the following folders:
path=/home/macstl/Documents
path=/home/macstl/Pictures
path=/home/macstl/joemc
path=/home/macstl/Downloads

But all of them are private shares requiring a username and password to access: " guest_ok=n"

The only way this is going to work is if you set up accounts for the remote user and supply samba passwords for those users. You also stated that both machines are using the same login id. So you need to add the login id and create a samba password for that login id. You do that this way:

Open **Terminal**
Type [B]sudo smbpasswd -a macstl

[/B](2) Your smb.conf file has been corrupted somehow[B].
[/B]> [global]
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
    name resolve order = lmhosts host wins bcast
    dns proxy = No
    wins support = Yes
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    [COLOR=Blue]comment = Users profiles
    path = /home/samba/profiles
    create mask = 0600
    directory mask = 0700
    browseable = No
    browsable = No[/COLOR]The lines in blue need to be commented out because they are being interpreted by samba as global options. You do that by adding a # in front of each of those lines:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Add a # in front of each of the blue lines so they look like this:
> [COLOR=Blue]#comment = Users profiles
     #path = /home/samba/profiles
     #create mask = 0600
     #directory mask = 0700
     #browseable = No
     #browsable = No[/COLOR]Save the file, exit gedit, and back in the Terminal type: **sudo service samba restart**

---

### Post by macstl on 2010-03-08
I made the changes and now I can see the shares . It makes me login to see them using my login joseph mcnamara +pw then i see the shares. then to get into a share it makes me login with user name macstl and then tells me i cant use two different logins for the same person. 
How can I get rid of all this login stuff?
thank you
macstl:p

---

### Post by macstl on 2010-03-08
I went into nautilus and gave the directorys all the permissions and guest so i got arrows in both directions above the icons of the directories and i can access from windows with no problem
thanks for all the help
How did i end up with two user names? When i login to ubuntu it is joseph mcnamara when i am in the system i am macstl.

---

