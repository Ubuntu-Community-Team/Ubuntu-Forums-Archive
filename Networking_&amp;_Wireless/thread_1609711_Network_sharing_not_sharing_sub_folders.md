---
title: "Network sharing not sharing sub folders"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by mongoose_za on 2010-10-30
Hi,

----What I have done---
I'm on Ubuntu 10.10. 
[LIST=1]
[*]I installed Samba and went Administration > Samba.
[*]Added a folder[Videos] to share(this folder is on an ext partition).
[*]I then went to the folder[Videos] Right+Click > Sharing Options
[INDENT][*]I selected 'Share this folder', 
[*]I put in a name and comment, 
[*]checked Allow others to create and delete files in this folder and 
[*]checked Guest Access.[/INDENT]
[/LIST]

---The Problem---
When I view this shared folder[Videos] from my Windows PC I can access it with no problems but when I try drill down into sub folders I get a permissions error. [Attached a screenshot of the error]

---What to do?---
If I share each folder separately then I can access them but obviously I'd like to share a folder and all it's contents. What am I doing wrong?

Thanks in advance.

---

### Post by Morbius1 on 2010-10-30
Step 1 is creating a Samba Classic Share.

Step3 is creating a Samba Usershare.

Two entirely different methods of creating samba shares.

Please post the output of the following commands:
```
net usershare info -list
```
```
testparm -s
```

---

### Post by mongoose_za on 2010-10-30
```
net usershare info -list
```
[videos]
path=/home/darren/Videos
comment=Videos
usershare_acl=Everyone:F,
guest_ok=y

[shared-10.10]
path=/home/darren/Shared-10.10
comment=Shared folder on Ubuntu 10.10
usershare_acl=Everyone:F,
guest_ok=y

```
testparm -s
```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Shared-10.10]"
Processing section "[Videos]"
Processing section "[toby]"
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

[Shared-10.10]
	comment = Shared folder on Ubuntu 10.10
	path = /home/darren/Shared-10.10
	read only = No
	guest ok = Yes

[Videos]
	comment = Videos
	path = /home/darren/Videos
	read only = No
	guest ok = Yes

[toby]
	comment = toby
	path = /media/Multimedia/Video/toby
	read only = No
	guest ok = Yes

---

### Post by elico on 2010-10-30
in the global section you have
you should add the security parameter as "user"
and make sure that you are using the correct user.

---

### Post by Morbius1 on 2010-10-30
I personally would get rid of the userhsares just because I don't like redundant sharing using 2 different methods but the nature of your problem isn't samba it's linux file permissions.

I guess the fastest way around your problem since all your shares are guest accessible is this:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line in the [COLOR=Blue]**[global]**[/COLOR] section of smb.conf:
```
force user = your-user-name
```[COLOR=Blue]*Change "your-user-name" to your actual login user name on that box*[/COLOR]

Save smb.conf, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```You should be able to drill down from any of your shares.

---

### Post by Morbius1 on 2010-10-30
> **elico said:**
> in the global section you have
you should add the security parameter as "user"
and make sure that you are using the correct user.
security = user is there by default. Theres no reason to add it.

---

### Post by Morbius1 on 2010-10-30
I've got to shut down for the night so just in case the force user line is confusing an example would be if I logged in as morbius and shared "Videos" then the force user line would be:
```
force user = morbius
```Don't forget to restart smbd.

---

### Post by mongoose_za on 2010-10-30
Here is my updated
```
testparm -s
```

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Shared-10.10]"
Processing section "[Videos]"
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
	force user = darren

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Shared-10.10]
	comment = Shared folder on Ubuntu 10.10
	path = /home/darren/Shared-10.10
	read only = No
	guest ok = Yes

[Videos]
	comment = Videos
	path = /media/Multimedia/Video
	force group = darren
	read only = No
	guest ok = Yes

I added the force user = darren to my [global] settings in my smb.conf. I still have the same issue though. From my Windows machine I'm able to access the root of the shared dir but when I try drill down I get the permission error. When I access the shared folder I'm not asked for any credentials if that means anything.
Thanks for your help so far.

---

### Post by mongoose_za on 2010-10-30
I've realised that the Video folder I'm trying to share belongs to 'root' and not 'darren'. 
I've tried 
```
sudo chown -R darren /media/Multimedia/Video/
```
but I can't seem to take ownership of my Videos folder. That is definitely the problem to this sharing issue though.

---

### Post by mongoose_za on 2010-10-30
I just read this [here]("http://www.uluga.ubuntuforums.org/showthread.php?t=1411263&page=2")
[I][INDENT]
The problem here was that the folder I wanted to change ownership of was where a NTFS partition was mounted - and I discovered eventually that NTFS doesnt have the same file permissions as ext3... so I don't know if there's a way to work around this and keep the NTFS format.. but as for me, I just formated the partition in ext3 after doing apropriate backups, etc...[/INDENT][/I]

Here's the output of my ```
ls -l /media/Multimedia/Video/
```

[INDENT]drwxrwxrwx 1 root root 12288 2010-05-29 23:35 Comedy
drwxrwxrwx 1 root root  4096 2010-10-12 23:57 Documentaries
drwxrwxrwx 1 root root  4096 2010-10-12 21:52 HD Movies
drwxrwxrwx 1 root root  4096 2010-10-12 23:57 Magic
drwxrwxrwx 1 root root     0 2010-10-12 21:56 Modern Family
drwxrwxrwx 1 root root 98304 2010-10-13 00:13 Movies
drwxrwxrwx 1 root root  4096 2010-10-13 00:09 Music Videos
drwxrwxrwx 1 root root     0 2010-10-12 21:56 Ratatouille
-rwxrwxrwx 1 root root 12800 2010-05-29 23:53 Thumbs.db
drwxrwxrwx 1 root root  4096 2010-10-13 00:11 toby
drwxrwxrwx 1 root root 16384 2010-10-08 17:13 TV Series[/INDENT]

Clear to see that my folder is under root ownership. But seeing as this is an NTFS drive how can I take ownership?

My fstab looks like this at that moment.
[INDENT]#Entry for /dev/sdd5 :
UUID=7D32D4D645A72FAA	/media/Multimedia	ntfs-3g	defaults,nosuid,nodev,locale=en_ZA.UTF-8	0	0[/INDENT]

---

### Post by mongoose_za on 2010-10-31
To change ownership of my NTFS partition I edited the following line in fstab.
```

#Entry for /dev/sdd5 :
#UUID=7D32D4D645A72FAA	/media/Multimedia	ntfs-3g	defaults,nosuid,nodev,locale=en_ZA.UTF-8	0	0
#EDIT: Entry for /dev/sdd5 :
UUID=7D32D4D645A72FAA /media/Multimedia		ntfs 	defaults,umask=007,uid=1000,gid=1000,relatime   0       0

```

Then I added force user = darren to [global] as well as make the following change in my smb.conf
```

[Videos]
	comment = Videos
	path = /media/Multimedia/Video
	writeable = yes
	browseable = yes
	guest ok = yes
	force user = darren
	force group = darren

```

The sharing is now working correctly. Thanks for your help. Much appreciated.

---

