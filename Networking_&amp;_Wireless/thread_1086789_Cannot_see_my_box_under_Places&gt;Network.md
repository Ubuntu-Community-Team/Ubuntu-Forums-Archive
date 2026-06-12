---
title: "Cannot see my box under Places&gt;Network"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by ogger on 2009-03-04
I am trying to share my printer on my Linux Box with my Windows Box, but I think I have a bigger issue as I cannot see both computers under Places>Network. I don't think it is my SMB.CONF file, which I simplified and looks like this:

```
[global]
	workgroup = Peter
	netbios name = Peter
	server string = Peter Server (Samba, Ubuntu)
	security = user
	encrypt passwords = yes
	local master = no	
[homes]
	comment = Home Directories
	browseable = yes
	writable = yes	
[printers] 
	comment = All Printers
	browseable = yes
	path = /var/spool/samba
	printable = yes
	guest ok = yes
	writeable = yes
	create mask = 0700
[print$] 
	comment = Printer Drivers
	path = /var/lib/samba/printers
	browseable = yes
	writeable = yes
	guest ok = yes

```

What else could it be?

---

### Post by Kellemora on 2009-03-04
Hi Oggr

There is a major bug in Nautilus that's been there for at least 3 years that I know of!

That don't mean your LAN is down or that you cannot access your shares the manual way.

After you go to Places/Network, Up at the top is a tab marked GO, open it and select LOCATION then enter the IP of the machine you are trying to get to.  You would use the format: this is only an example IP number. 
```
smb://192.168.1.100/
```
Naturally the IP number will be whatever machine and IP numbers you are using there.
It will then open your shares in Nautilus and they should appear the same as if Places/Network was working properly.

Mine would work for like 3 days, then not work for 2 days, then work again for 3 or 4 days, then quit again, without making any changes to anything.  However, since I moved up to 64 bit Ubuntu Places/Network as not worked since.

You may want to install SMBTREE and if not already installed, SMBCLIENT.
IF you have SMBFS installed, REMOVE IT, it causes about 1/3 of your shares to NOT show.

SMBTREE is used in command line to show your shares, just type smbtree and hit enter.  That's the fastest test I know to make sure all of your shares are really visible through Samba.  If you can seem them there, then everything is working correctly and you can get to them using Go/Location and the IP number.

TTUL
Gary

---

### Post by chelrob on 2009-03-04
Try this:
[http://ubuntuforums.org/showthread.php?t=1086208](http://ubuntuforums.org/showthread.php?t=1086208)

---

