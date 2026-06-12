---
title: "Mounting Network Drives"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by Burky on 2009-12-29
I know how to mount a network drive on Ubuntu from a Windows computer, but I have the external on an Ubuntu machine now. I would like to mount it on another Ubuntu machine over the network. This should be possible right? I just don't know how. Can you guys please help me?

---

### Post by Morbius1 on 2009-12-29
Let me make sure I understand what you want to do.

You have an external usb drive ( let's call it Fred ) connected to your linux machine ( let's call it Ubuntu1 ). Now you want to access that drive from another linux machine ( let's call it Ubuntu2 ). If I have that right then use the following as a template substituting real names for mine.

I'm assumming here that you have not edited fstab to mount Fred on Ubuntu1 but simply insert Fred and have it automount to /media/Fred and that the filesystem on that usb device is FAT32 or NTFS.

***On Ubuntu1***
Go to Nautilus > Right Click on /media/Fred > Select "Sharing Options" > Select all the boxes ( Share this folder, Allow write, and guest access ) then select "Create Share"

Here's the problem at this point. When Fred mounts, Ubuntu1 sets ownership to you but it sets permissions to allow only you to read and write to it and no one else. But when you shared Fred you set it to allow guest access. Well it won't work.

Here's the next step:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**
Add the following line in the[COLOR=Blue]** [global]**[/COLOR] section of smb.conf:
```
force user = your_Ubuntu1_user_name
```[COLOR=Blue][I]Substitue your real login username here

[/I][COLOR=Black]Save the file, close gedit, and back in the Terminal type [B]sudo service samba restart

[/B]Wait a few minutes ( when you restart samba, the network has to reset itself :) )

Now see if you can access Fred from Ubuntu2



[/COLOR][/COLOR]

---

### Post by Burky on 2010-01-23
I'm sorry I took me a LONG time to reply, thanks though.

Um I tried it with Ubuntu Karmic Koala being the host and the Xubuntu Karmic Koala the one trying to read it. It didn't work.. any ideas?

---

### Post by adam814 on 2010-01-23
Might I suggest as an alternative using NFS?  I'm not sure if there are Windows clients for it, but it works pretty seamlessly between *nix machines.  At least it's something to try if Samba proves difficult.

[https://help.ubuntu.com/community/SettingUpNFSHowTo#Installation%20and%20Configuration]("https://help.ubuntu.com/community/SettingUpNFSHowTo#Installation%20and%20Configuration")

I just tried it out myself to make sure I could with an NTFS drive.  I can share it just fine, but as I should have expected permissions don't work (stuck at 777).  I'm sure there's a way to change that other than sharing it read-only, but I'm not sure how at the moment.

If that would present a problem on your network you might want to stick it out with Samba.

---

### Post by Morbius1 on 2010-01-23
> It didn't work.. any ideas?

What didn't work?

The other machine can't see the share?

Or the other machine is denied access to the share?

How are you mounting the share?

What kind of error messages are you receiving?

On the machine that has the share you want to access post the output of the following commands:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**

---

### Post by Burky on 2010-01-23
Alright, I did what you told me to do as far as Ubuntu1.

But Xubuntu2, I didn't even know where to find the network on Xfce XD, so it's not really fair to say it didn't work I guess..

Ubuntu1

```
david@david-desktop:~$ net usershare info
david@david-desktop:~$ testparm-s
testparm-s: command not found
david@david-desktop:~$ testparm -s
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
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	force user = david

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

```

Xubuntu2:

```
david@david-laptop:~$ net usershare info
david@david-laptop:~$ testparm -s
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
```

---

### Post by dmizer on 2010-01-23
> **Burky said:**
> I know how to mount a network drive on Ubuntu from a Windows computer, but I have the external on an Ubuntu machine now. I would like to mount it on another Ubuntu machine over the network. This should be possible right? I just don't know how. Can you guys please help me?

Take a look at the second link in my sig. :)

---

### Post by Burky on 2010-01-23
> **dmizer said:**
> Take a look at the second link in my sig. :)

I've used that lovely tutorial before to mount a windowshare on an Ubuntu machine. Never thought it would work with both Ubuntu machines. I'll try it. Thanks

---

### Post by Morbius1 on 2010-01-23
Based on the output of net usershare and testparm you have not shared anything so there is nothing for the remote machine to mount.

Why not go into Nautilus, right click on say /home/david/Documents , Sharing Options, check off all the boxes, and create a share first.

---

### Post by Burky on 2010-01-23
I swore I thought I already did that, oh well. So! How do I get Xubuntu to see it.

Ubuntu1 Now looks this:

```
david@david-desktop:~$ net usershare info
[external]
path=/media/EXTERNAL
comment=
usershare_acl=Everyone:F,
guest_ok=y

david@david-desktop:~$ testparm -s
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
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	force user = david

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

```

---

### Post by Morbius1 on 2010-01-23
I know nothing about Xubuntu but I did find this:

[B]How to: Xubuntu - Thunar Native Windows Network Browsing
[/B][http://ubuntuforums.org/showthread.php?t=304131&page=3](http://ubuntuforums.org/showthread.php?t=304131&page=3)

It's rather old so I don't even know if it's still applicable.

Your only other option is dmizer's HowTo. His method is classic and will work on any linux desktop environment.

---

