---
title: "SAMBA workgroup problem?"
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by rhcm123 on 2009-02-14
This isn't a really major problem, just a tiny thing i would like fixed. :)
I was used to being able to go to Places -> Network -> Windows Network -> USSR (My workgroup) and see all the computers in the USSR workgroup. Now, the workgroup dosent' even show up!

I think this is because i recently lost my smb.conf file on my server that was the master for this workgroup. Does anybody know how to make this work again. (read: make my server the USSR workgroup master, i guess?)

---

### Post by rhcm123 on 2009-02-28
Bump for justice? Anybody?

---

### Post by albinootje on 2009-02-28
> **rhcm123 said:**
>  I think this is because i recently lost my smb.conf file on my server that was the master for this workgroup. 

How did you set up Samba before on your server ? With a "GUI" like webmin or swat, or by CLI instructions ?

Here's a good howto : [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by rhcm123 on 2009-03-02
> **albinootje said:**
> How did you set up Samba before on your server ? With a "GUI" like webmin or swat, or by CLI instructions ?

Here's a good howto : [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

I wrote it by hand, and I think i followed that guide. I also got help here on the forums.

My smb.conf
```
# CONFIG FILE FOR SAMBA
# WRITTEN BY USSR
# LAST MODIFIED 7 JAN/09

# Global parameters
[global]
	log file = /var/log/samba/log.%m
	load printers = yes
	guest account = nobody
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	interfaces = 192.168.2.193
	map to guest = Bad User
	use client driver = yes
	wins support = true
	dns proxy = No
	netbios name = USSR-MOSCOW
	server string = SMB system on USSR-MOSCOW
	printing = cups
	default = global
	local master = Yes
	workgroup = USSR
	os level = 20
	printcap name = cups
	security = share
	max log size = 50

# /SHARE CONFIGS
[share]
	path = /share
	valid users = ussr elisabeth fred carol nobody
	read only = No
	browseable = yes
	comment = Main share directory on USSR-MOSCOW.
	create mask = 0777
	directory mask = 0777

# BACKUP DRIVE CONFIGS
[backup]
	path = /media/backup
	valid users = root
	read only = No
	browseable = yes
	comment = Backup Drive on USSR-MOSCOW. root Access Only.
	create mask = 0777
	directory mask = 0777

# PRINTER SETTINGS
[printers]
	comment = Printers on USSR-MOSCOW
	browseable = no
	path = /printer
	printable = yes
	force user = nobody
	public = yes
	writable = no
	create mode = 0700

# CDROM SHARING
[cdrom]
	comment = CD on USSR-MOSCOW
	read only = yes
	writable = no
 	locking = no
	path = /cdrom
	public = yes



```

---

### Post by albinootje on 2009-03-02
> **rhcm123 said:**
>  My smb.conf

Thanks for posting that. 
I just compared it with the smb.conf from my local file server, and I don't see anything unusual.
But I tried -> Places -> Network, and then I had to fill in smb://my_local_file_server_name (which I have defined in /etc/hosts) before the shares became visible.

---

### Post by rhcm123 on 2009-03-03
> **albinootje said:**
> Thanks for posting that. 
I just compared it with the smb.conf from my local file server, and I don't see anything unusual.
But I tried -> Places -> Network, and then I had to fill in smb://my_local_file_server_name (which I have defined in /etc/hosts) before the shares became visible.

yes, but my question is that i used to have the icon right there instead of having to manually type it

---

### Post by chelrob on 2009-03-03
Samba and smb.conf have nothing to do with Ubuntu's ability to view other computers on the network.  You can uninstall the samba package and delete the smb.conf and still see the network.  You're problem is somewhere else.

This is what was causing the problem on my system:
[http://ubuntuforums.org/showthread.php?t=1086208](http://ubuntuforums.org/showthread.php?t=1086208)

 - peace

---

### Post by Kellemora on 2009-03-04
Hi RHCM

If you are talking about NOT seeing your shares in Places/Network, but you can get to them using Go/Location and the IP number.

This means everything IS working correctly!

There has been a major BUG in Places/Network that dates back to complaints about if for over 3 years now.

I gave up holding my breath for someone to take a look at the problem!

My shares would show for like 3 days, then not show for 2 days, then show for 3 or 4 days, not show again for 2 or 3 days, without making any changes of any kind.  That's just the way it is!
And ever since adding some 64 bit machines, Places/Network has never worked since here!

At least it works well enough that I can get to the shares manually all the time!

Good Luck

TTUL
Gary

---

### Post by Centx on 2009-03-04
I have a similar (or maybe the exact same) problem here.

Lol, I actually tried to set up a network here, running in circles for hours with samba and smb.conf to get the shares to show up in "places > network"

I'm astonished over how badly this works, really. From now on, I'll probably just use "places > connect to server", but on networks without nodes with static IP's, this isn't feasible at all.

Trying to get my setup right now =).

---

### Post by chelrob on 2009-03-05
Samba and smb.conf have nothing to do with Ubuntu's ability to view other computers on the network.

---

### Post by rhcm123 on 2009-03-07
Well, it's kinda working... the shares are defined and automatically displayed on Windows computers, but on ubuntu/other linux variants i have to manually define them in /etc/fstab

Odd, but i don't really care as they auto mount at boot anyways.
I was just wondering why on earth this was occouring... and why windows was doing somthing right and linux wasnt :O

I've read so many different solutions here on the formus it seems to me that it may be just simpler to let it be - it works manually and i can set up client machines to do this automatically... :lolflag:

---

