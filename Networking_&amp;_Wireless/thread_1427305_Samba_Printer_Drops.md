---
title: "Samba Printer Drops"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by tracyandskye on 2010-03-11
I have a Samba file server with one windows & one Ubuntu workstation.  The Ubuntu workstation is a Samba print server.  The problem is that the XP machine cannot access the printer.  If I restart Samba on the print server it works again.  There may be a pattern but I havn't figured it out yet.  Here's my file:

[global]
	workgroup = voodoonet
	netbios name = Bob
	name resolve order = bcast host lmhosts wins
	server string = 
	map to guest = Bad User
	local master = yes
	os level = 33
	usershare allow guests = Yes
	usershare max shares = 100
	usershare owner only = False
	printing = cups
	printcap name = cups
	printcap cache time = 750
	cups options = raw
	load printers = yes
	use client driver = yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	printable = Yes
	create mask = 0700
	browseable = No
	guest ok = Yes

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	browseable = yes
	read only = yes
	guest ok = no

[Documents]
	path = /home/bob/Documents
	writeable = yes
	browseable = yes
	guest ok = yes

---

### Post by suseendran.rengabashyam on 2010-03-12
Hi,

You can refer this thread for a workaround

[http://ubuntuforums.org/showthread.php?t=1386531](http://ubuntuforums.org/showthread.php?t=1386531)

Hope this helps.

---

### Post by tracyandskye on 2010-03-12
Thanks but in my case it seems like it works after boot (not entirely sure), but it definitely drops out again after I have already manually restarted Samba.  I will now be able to use the status command though, to help determine what is happening.

---

### Post by tracyandskye on 2010-04-08
I don't know if I was mistaken or something changed, but that fix worked.  Thanks for the help.

---

