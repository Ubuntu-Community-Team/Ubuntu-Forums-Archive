---
title: "Samba and Windows Networking"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by PeteLong on 2011-03-09
***[disclaimer always assume I'm thick as mince and know nothing!]***

OK Ive managed to install samba, I've shared a folder (the public folder in my home drive).

I can access from a Windows 7 machine via \\ubuntu\public 

I can put files in the folder form the ubuntu machine and edit them on the windows box.

I can put files in the folder/share from the Windows box but then I cannot edit them on the Ubuntu machine (they are read only and have a "Lock" over them).

I can fix this by going to the properties of the file/folder in Windows and manually assigning "Everybody" full control (then the lock disappears and all is well.)

- I want read/write access to all the folders contents from both machines all the time (security is **NOT** a concern I **WANT **the permissions wide open) what am I doing wrong?

Pete:D
[PeteNetLive]("http://www.petenetlive.com")

---

### Post by Morbius1 on 2011-03-09
We don't know what method of samba sharing you are using - Userhsare ( though Nautilus ) or Classic-share.

One quick way out of your situation is to add the following parameter to your smb.conf:
```
force user = morbius
```[COLOR=Blue]*Change morbius to the linux login user name on the box with the share.*[/COLOR]

Where you put that line depends on the method used to create the share. If you created the share using nautilus add it to the [global] section. If you created a classic-share then add it to the share definition itself.

If you have no idea what I'm talking about then post the output of the following commands so I can be more specific:
```
net usershare info --long
``````
testparm -s
```

---

### Post by PeteLong on 2011-03-09
Hi Thanks!

>>We don't know what method of samba sharing you are using

Apologies - This is how I set it up,
[http://www.youtube.com/watch?v=j2Ap_xGEZ3k](http://www.youtube.com/watch?v=j2Ap_xGEZ3k)

>>If you have no idea what I'm talking about then post the output of the following commands so I can be more specific:

No problem


pete@VMUbuntu:~$ net usershare info --long
[public]
path=/home/pete/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y

pete@VMUbuntu:~$ testparm -s
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

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
pete@VMUbuntu:~$ 

Pete

---

### Post by Morbius1 on 2011-03-09
Ok, you're using usershare so add the following to the [global] section of smb.conf:
```
force user = pete
```Then restart samba.

What force user will do is convert the guest remote user from "nobody" to "pete" so that all new files added will be owned by "pete".

---

### Post by PeteLong on 2011-03-09
OIC that makes sense! Hang on I'll give it a go...

---

### Post by PeteLong on 2011-03-09
Outstanding that worked perfectly! Thanks for your time and patience - kudos to you! :D

---

### Post by orsula on 2011-03-09
Excuse me for hijacking the thread, but I have an old lab instrument running Windows98 that I'd like to access. I use a CAT-5 cable (inverted) to connect it to my 10.10 Ubuntu (2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011 i686 GNU/Linux). 

Using the simple interface from Places > Connect to Server ... and using service type: Windows Share, I put the server and share names in the provided spots but I can never connect to the Windows98 box. The Win98 is set to not ask for any passwords and have anyone login to it. I always get the message "Cannot display location "smb://server/share/"

If I use a Win7 to connect to the older Win98 box and use 'Map Network Drive..' with \\server\share, I can always connect without a problem. Funny thing is that my work has a network mass storage drive that requires a user/pass that I can easily access from Ubuntu so I think my Samba installation is OK. Any ideas what is going on with the win98 box?

Thanks very much in advance,
Gideon

```
cpcc@sensors:~$ samba -b -V
Build environment:
   Build host:  Linux vernadsky 2.6.24-27-server #1 SMP Fri Mar 12 01:45:06 UTC 2010 i686 GNU/Linux
Paths:
   BINDIR: /usr/bin
   SBINDIR: /usr/sbin
   CONFIGFILE: /etc/samba/smb.conf
   NCALRPCDIR: /var/ncalrpc
   LOGFILEBASE: /var/log/samba
   LMHOSTSFILE: /etc/samba/lmhosts
   DATADIR: /usr/share/samba
   MODULESDIR: /usr/lib/samba
   LOCKDIR: /var/lib/samba
   PIDDIR: /var/run/samba
   PRIVATE_DIR: /var/lib/samba/private
   SWATDIR: /usr/share/samba/swat
   SETUPDIR: /usr/share/samba/setup
   WINBINDD_SOCKET_DIR: /var/run/samba/winbindd
   WINBINDD_PRIVILEGED_SOCKET_DIR: /var/run/samba/winbindd_privileged
   NTP_SIGND_SOCKET_DIR: /var/run/samba/ntp_signd

```
```
cpcc@sensors:~$ testparm -s
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

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

```

---

### Post by PeteLong on 2011-03-10
Once again thanks to Morbius1

Heres how I got it working


[Sharing Files from Ubuntu to Windows]("http://www.petenetlive.com/KB/Article/0000412.htm")

Pete
[PeteNetLive]("http://www.petenetlive.com")

---

