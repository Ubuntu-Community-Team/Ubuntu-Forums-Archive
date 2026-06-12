---
title: "Networking Ubuntu 10.10 and Windows computers"
date: 2011-04-20
forum: Networking &amp; Wireless
---

### Post by jacob-heller on 2011-04-20
Hey all,

I'd like my Windows computer to see certain files on my Ubuntu machine (specifically, I'd like my Windows computer to be able to play videos hosted on my Ubuntu machine). I've been struggling for the last few days, trying literally every tutorial and forum post ever written about Samba, etc., and so I finally figured I'd give up and turn to the forum.

Here's the full situation:
- My Windows XP or Windows 7 computers do not see my Ubuntu machine *at all*. It's not showing up in my network places/workgroup computers, and when I type in \\ubuntuipaddress, it gives me an error saying that "Windows cannot find" the IP address.
- Samba is installed on my ubuntu machine.
- I can right-click on a folder, choose "Sharing Options," check all the right boxes to no apparent effect.
-  I can go to System > Administration > Samba and add folders to share, also without any apparent effect.
- When I run "net usershare info --long" I get:
```
[public]
path=/home/jakeandmiki/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y

[videos]
path=/home/jakeandmiki/Videos
comment=
usershare_acl=Everyone:F,
guest_ok=y
```
- I've tried to edit the smb.conf file a million times, following various tutorials and tips. When I do testparm, here's what I get:
```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[videos]"
Processing section "[Home]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	netbios name = 
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = bcast host lmhosts wins
	printcap name = cups
	os level = 33
	dns proxy = No
	usershare allow guests = Yes
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d
	cups options = raw

[homes]
	comment = Home Directories
	read only = No
	create mask = 0775
	directory mask = 0775

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[videos]
	path = /home/jakeandmiki/Videos
	guest ok = Yes

[Home]
	comment = our home folder
	path = /home/jakeandmiki
	read only = No
	guest ok = Yes

```
- I have added smbpasswd -a USERNAME, where USERNAME is my Ubuntu username. Just to be uber-cautious, I've changed my Windows username to precisely the same name as my Ubuntu name. 

I've tried so many things at this point, it might be that the best advice one can start with is how I can wipe the slate clean so we're all starting from the same place. It's quite possible I broke something while trying to fix it.

Help would be greatly, greatly appreciated. Also, I am not particularly attached to Samba or anything -- any (easier) alternatives for me to access my media files would also be appreciated.

Feel free to ask me to post any more information that might help you get to the bottom of this.

Thanks all. 

Jake

---

### Post by headvampyre@hotmail.co.uk on 2011-04-22
Are you getting the IP right?

Also, im pretty sure you MUST configure:

netbios name = 

for anything to work, as Samba uses NetBIOS for browsing. Set that parameter to your computer name and check if it works.

---

### Post by dandnsmith on 2011-04-22
I've always had a line to set the workgroup the same as my Windows workgroup (you need to check what that is, and I also have a hosts allow line to define my local "group"

---

### Post by jacob-heller on 2011-04-23
Okay, the problem is solved (mostly). The *real* problem was that I had to type in \\UBUNTUIPADDRESS\**SHARENAME** (not just \\UBUNTUIPADDRESS), and the window popped open just fine. The key is that the SHARENAME must be the name you name you **assign** the folder when you right-click > sharing options, not the folder as it is actually named on your computer. 

This all worked before I added the netbios name, and so I never made that change. 

Now I can share through right-clicking a folder and choosing share options or by adding the folder in my Samba administrator panel. Inexplicably, I can now even do \\UBUNTUNAME\ and Windows finds my computer, even though that never worked before. For what it's worth, I changed my computer name from something really complicated with dashes and numbers to just "mediaserver", so maybe that helped (?)

In the hopes that this will help someone, here's the complete contents of a working smb.conf file. Note that there is no longer any workgroup variable set; how or why this works is beyond me, but my workgroup at home is called WORKGROUP, so maybe it just defaults to that or something... Also, in System > Administration > Samba > Preferences > Server Settings, my workgroup is set to workgroup.

```
[global]
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = bcast host lmhosts wins
	printcap name = cups
	os level = 33
	dns proxy = No
	usershare allow guests = Yes
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d
	cups options = raw

[homes]
	comment = Home Directories
	path = /home
	read only = No
	create mask = 0775
	directory mask = 0775
	guest ok = Yes

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

net usershare info --long now spits out the one folder I truly hope to share, my home directory:

```
[home]
path=/home/MYUSERNAME
comment=our home folder
usershare_acl=Everyone:F,
guest_ok=y

```

Note that when I am on my Windows computer, I just type in \\MYCOMPUTERNAME\home, and NOT \\MYCOMPUTERNAME\MYUSERNAME or something of the sort to get to the file I want; Windows won't find the latter.

Hope any of this helps. For those of you struggling to find a solution to sharing with Ubuntu 10.10, please feel free to ask here and I'll respond with my settings to see how our settings differ.

Best,
Jake

---

### Post by jacob-heller on 2011-04-23
By the way, the above post slightly overstated how much my solution is actually working. In fact, I cannot access my Ubuntu machine from my XP computer, only from my Windows 7 computer. Go figure. Any reasons that might be the case?

---

### Post by Morbius1 on 2011-04-23
You are using a rather odd combination of Classic-share and Usershare in your setup.

A note on the [homes] section. It was created as a meta-share in much the same way as the [printers] section was created. Neither one of them actually point to to an actual path ( or printer ).

It usually takes the following form:
> [homes]
    comment = Home Directories
    valid users = %S
    create mask = 0700
    directory mask = 0700
    read only = yesYou will notice it has no path and it's not browseable like a normal share because it's created "on the fly" at the moment the remote user asks for it using the [homes] definition as a template .

On a remote linux machine you have to ask for it explicitly:
```
nautilus smb://192.168.0.100/user-name
```On a remote Windows machine you can set this up to work like magic using a flaw in the design of Windows itself. Windows will actually pass it's login user name and password when it connects to a remote machine. If you set up a user on the Linux server with the same name and the same samba password then the remote Windows user will have access to the linux share automatically.

By setting up guest access in the homes section ( btw - there's a system administrator somewhere in the world that has just fainted at seeing that statement ) you defeated the purpose of the homes section. 

If it were me I would remove the [homes] section completely and use Usershare ( right click a folder in Nautilus > Sharing Options....) by itself. I really wouldn't share the whole home directory or even your own home directory  ( in fact usershare will give you an error message if you try to do the latter but it's easy to just rename it ) but that's up to you.

---

### Post by jacob-heller on 2011-04-23
Duly noted. I removed the homes section from the smb.conf file and restarted samba. Thanks for the advice.

---

