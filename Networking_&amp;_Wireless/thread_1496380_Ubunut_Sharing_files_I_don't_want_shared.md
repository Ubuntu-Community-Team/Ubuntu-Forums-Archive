---
title: "Ubunut Sharing files I don't want shared"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by randallsstevens on 2010-05-29
I am using the latest ubuntu 10.04. Which we have a network of 3 XP pc's and one ubuntu. I have networking set up between them which works fine except that ubuntu is sharing my main &quot;folder&quot; where I keep all of my stuff. This is on a separate partition if that makes any difference.   So I have a shared folder which is meant to be shared and shows up as shared. But my other partition is not supposed to be shared and doesn't show up as shared any where, except that everyone on the network can see it and access it. When I right click the partition and click properties-->sharing it's greyed out and I have the options to share it. When I look it samba only my Shared folder shows up and not this partition..  This wasn't happening before I upgraded to 10.04 from 9.10.  Please help, I'm an ubuntu noob but I really need this &quot;not shared&quot; partition to not be shared!

---

### Post by Morbius1 on 2010-05-29
Well, after reading one zillion posts on samba not working at all this is the first time I've read one where samba is sharing too much.

Please post the output of the following commands so we can see how things are set up:

```
net usershare info
sudo net usershare info
testparm -s
```

---

### Post by randallsstevens on 2010-05-29
Thanks for your reply:

Heres what they output : 
net usershare info

[sda5]
path=/media/sda5
comment=
usershare_acl=Everyone:R,
guest_ok=n

info_fn: file /var/lib/samba/usershares/shared2 is not a well formed usershare file.
info_fn: Error was Path is not a directory.


**SDA5** is the partition I don't want shared.

sudo net usershare info

[shared]
path=/home/xxxx/Shared
comment=
usershare_acl=Everyone:F,
guest_ok=y

This is the shared I do want shared, and is working

testparm -s

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[Shared]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	netbios name = PUTNAMEHERE
	server string = Ubuntu
	security = SHARE
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	lanman auth = Yes
	client lanman auth = Yes
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

[Shared]
	path = /home/xxxx/Shared
	read only = No
	guest ok = Yes



I changed the netbios name to putnamehere ages ago, not had any problems until 10.04.

Thanks for your help, hope this output is useful.

---

### Post by Morbius1 on 2010-05-29
There's two methods of sharing folders in Samba: Classic-share ( smb.conf) and Nautilus-share ( var/lib/samba/usershares ). You're using both methods.

As a normal user go into Nautilus and right click /media/sda5 > Sharing Options - and "unshare" the folder.

You've also got /home/xxxx/Shared shared using both Classic-share and Nautilus-share but since they don't conflict let's just let that go for the time being.

There's no need to restart samba. So let's see if that eliminates the problem.

---

### Post by randallsstevens on 2010-05-29
Hi, 
     I tried toggling the "share this folder"  a few times (it was greyed out originally), Now SDA5 Still shows up in network but it asks for my password now, which is a big improvement!  How do I stop it from showing up in the network ? 

There's no "un-share this folder" so I assume you just meant uncheck the share this folder

Thanks,

---

### Post by Morbius1 on 2010-05-29
In a terminal type:
```
net usershare delete sda5
```

[COLOR=Blue]Note: this will delete the sharing of the directory not the directory itself.[/COLOR]

If that still doesn't remove the share then please post the output of the following:
```
ls -al /var/lib/samba/usershares
```

---

### Post by randallsstevens on 2010-05-29
:popcorn:  Wooot! It worked!   Thanks for taking the time to help me.

---

