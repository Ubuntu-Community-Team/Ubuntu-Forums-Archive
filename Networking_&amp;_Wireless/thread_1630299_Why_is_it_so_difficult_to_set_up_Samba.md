---
title: "Why is it so difficult to set up Samba"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by Milliways on 2010-11-25
Every time I set up a new Ubuntu I have problems getting Samba to work.
I now have it working, but my process seems to have little to do with the documentation.

1. I run shares-admin, which offers to install NFS & SMB.
2. shares-admin Shared Folders only offers NFS not SMB, although the General Properties tab allows me to set Workgroup
3. At this stage I give up and edit smb.conf
4. Windows can now see the share, but will not let me log on.
5. I have to run smbpasswd to change the user password.
6. Nautilus does not show the folders as shared.


Why does shares-admin offer SMB if it can't do anything with it?
Surely sharing home directories is so common that it should have an easier way of setting than editing smb.conf

---

### Post by vorlow on 2010-11-25
I have a similar problem. I have a Linux pc connected on a workgroup which has 3 more WIN XP machines, via a simple hab.

I set up unix accounts for all users in the workgroup and enable them in SAMBA. Each user logs one once with his/hers username-password and has access to common directories and his own (private)...

It works ok for a few minutes and then the users can not access their shared directories anymore (which reside on the linux machine) or manipulate shared files, unless the directories are set up to allow access to anyone.

It seems their credentials reset somehow...

I had to make all directories accessible by all via the normal share (right click on folder etc. etc.) and disable the samba accounts and functionality. Hence I can not have username/password access to individual directories which is what samba would allow us to do otherwise...

Any thoughts? Is it a=the firewall? Is it something in smbd.conf???


Best,
Costas

---

### Post by luvshines on 2010-11-25
> **Milliways said:**
> Every time I set up a new Ubuntu I have problems getting Samba to work.
I now have it working, but my process seems to have little to do with the documentation.

1. I run shares-admin, which offers to install NFS & SMB.
2. shares-admin Shared Folders only offers NFS not SMB, although the General Properties tab allows me to set Workgroup
3. At this stage I give up and edit smb.conf
4. Windows can now see the share, but will not let me log on.
5. I have to run smbpasswd to change the user password.
6. Nautilus does not show the folders as shared.


Why does shares-admin offer SMB if it can't do anything with it?
Surely sharing home directories is so common that it should have an easier way of setting than editing smb.conf

Assuming that we'll go ahead with smb.conf way, can you post output of ```
testparm -s
```

---

### Post by Milliways on 2010-11-25
> **luvshines said:**
> Assuming that we'll go ahead with smb.conf way, can you post output of ```
testparm -s
```

NOTE This is now working.

```
[global]
	workgroup = ******NET
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

[homes]
	comment = Home Directories
	browseable = No

[DropBox]
	path = /home/DropBox
	read only = No
	guest ok = Yes

[FileSystem]
	path = /
	guest ok = Yes
```

---

### Post by Morbius1 on 2010-11-25
> NOTE This is now working.So this was not a request for help but more a detailed account of your difficulties?

> 1. I run shares-admin, which offers to install NFS & SMB.
2. shares-admin Shared Folders only offers NFS not SMB, although the General Properties tab allows me to set Workgroup
3. At this stage I give up and edit smb.confshares-admin doesn't really work anymore - at least not in Ubuntu. If you want to do Samba Classic shares then you need to install:
```
system-config-samba
```> 4. Windows can now see the share, but will not let me log on.
5. I have to run smbpasswd to change the user password.If you have your shares set up to require username and password then that's the way it should work.
>  6. Nautilus does not show the folders as shared.For classic samba sharing Nautilus never did change the icon to show that it was shared. Samba's Usershare ( aka Nautilus-share ) does that but not Classic share.

---

### Post by Milliways on 2010-11-26
> **Morbius1 said:**
> So this was not a request for help but more a detailed account of your difficulties?

shares-admin doesn't really work anymore - at least not in Ubuntu.

My original posting said I now have it working, but asked a couple of questions 

> Every time I set up a new Ubuntu I have problems getting Samba to work.
I now have it working, but my process seems to have little to do with the documentation.

> Why does shares-admin offer SMB if it can't do anything with it?

I don't understand why I have to run smbpasswd to change the user password.
The Windows and Ubuntu usernames and passwords are identical, and this works by default in Windows.
This does not seem to have been mentioned in any of the documentation I read.

NOTE when running smbpasswd I had to enter the "old" password, then the "new" - which were identical.

Next time (11.04) I will install system-config-samba

---

### Post by jonandrews on 2010-11-26
Although Samba is indeed difficult to set up if you need detailed control , of security, say, I have to say that in recent Ubuntu releases simple networking on a windows network can be achieved in about 14 clicks without going anywhere near samba.conf.  I've writen a guide to the process:
[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by Morbius1 on 2010-11-26
> I don't understand why I have to run smbpasswd to change the user password.
The Windows and Ubuntu usernames and passwords are identical, and this works by default in Windows.The Windows and Linux local login user names and passwords may be exactly the same but Samba doesn't use the local login username and password. However samba can be made to use them if that's what you want.

The procedure for authenticating a remote user to your share has two steps:

[1] Create a local user on the server with the share that corresponds to the remote user that you want to gain access.

[2] Create a samba password for that user to use to gain access. 

It's been that way for 18 years.

Remember this is Linux not Windows. Linux considers it strange that anyone would create a samba user / password that matches exactly the local login user name and password of the remote user. To do so would mean the share owner now knows how to login to the remote users local physical machine.

---

### Post by SeijiSensei on 2010-11-26
Take a look at /etc/samba/smbpasswd and at /etc/passwd.  Notice that the hashes are *extremely* different?  That's because Windows uses a different password hashing mechanism than Unix.

Out of the box, samba exports all the home directories and the printers automatically.  You just need to add the users to smbpasswd, and you're good to go.  If you want to create a custom share, then you'll need to understand smb.conf.  That's not that unusual, though; people setting up servers are used to editing configuration files.

---

