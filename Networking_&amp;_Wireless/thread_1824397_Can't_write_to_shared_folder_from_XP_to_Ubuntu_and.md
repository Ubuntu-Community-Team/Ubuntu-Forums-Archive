---
title: "Can't write to shared folder from XP to Ubuntu and vice versa"
date: 2011-08-13
forum: Networking &amp; Wireless
---

### Post by Mezgrman on 2011-08-13
The title says it all: I have two folders which I share in Ubuntu (10.10), one of them is "public", so I set it to allow guests to create/move/delete files in the folder. Then there is my mother's PC running Windows XP Professional (also one shared folder with write access). When I was using Windows 7, I could create/delete/edit files on my mother's shared folder but now, using Ubuntu, I can only read from it. Same with the shared folder in Ubuntu, I can only read it from XP but not write to it.

Any help would be greatly appreciated. :D

---

### Post by Morbius1 on 2011-08-13
From the Linux box please post the output of the following commands: 
```
net usershare info --long
```
```
testparm -s
```

---

### Post by Mezgrman on 2011-08-13
```
[public]
path=/home/mezgrman/Öffentlich
comment=Öffentliche Dateien auf meinem Notebook unter Linux.
usershare_acl=Everyone:F,
guest_ok=y

[brony_lib]
path=/home/mezgrman/My Little Pony
comment=My collection of pony stuff.
usershare_acl=Everyone:R,MEZGRMAN\(null):F,
guest_ok=y
```

and

```
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

### Post by Morbius1 on 2011-08-13
Unfortunately, everything looks textbook correct.

Maybe it's a permissions problem on the target. What does this look like:
```
 ls -dl /home/mezgrman/Öffentlich
```It has to come back with this:
> drwxrwxrwxIf it doesn't then make it that:
```
chmod 777 /home/mezgrman/Öffentlich
```

---

### Post by Mezgrman on 2011-08-13
```
drwxrwxrwx 7 mezgrman mezgrman 4096 2011-08-11 16:21 /home/mezgrman/Öffentlich
```

Do you have any tips what I should do at the Windows PC?

---

### Post by Mezgrman on 2011-08-13
I just noticed something strange: From Ubuntu, I can rename and delete files and directories, but I can NOT create new files or directories. Now I'm even more confused :confused:

---

### Post by Mezgrman on 2011-08-14
Seems that I have almost fixed it now. I had to set the **local** permissions of my shared folder so that everyone could edit/create/delete files. Now I have full access to this folder from XP.
I also changed the workgroup name of my Linux computer to match the name that is set on the Windows PC. And I did the same thing I did on the Linux box on the Windows box, I gave everyone full access to the shared folder.
It seems that I've had full access to the Windows share from the beginning – as I said, I could rename and delete files and folders, but when I wanted to create a new file/folder or paste something in Nautilus, the appropriate entries in the context menu were greyed out. I just tried the drag&drop method to paste a file to the windows share and it worked. So this seems more like a problem in Nautilus to me... anyway, the original problem is solved now. :)

---

