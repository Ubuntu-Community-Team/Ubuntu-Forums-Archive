---
title: "new one for the samba"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by evilbuntu on 2009-07-31
well thanks to everyone my samba is running again, then it stopped and i just downloaded a bunch of samba updates and its working again. so i guess it is just temperamental.

heres a new one though i have been researching and cant seem to get. with users, machine names and the work group.

i have been trying to give my user on my ubuntu tower admin rights on my xp machine BUT, my xp machine CANT see my linux tower in the workgroup.

ubuntu sees the XP machin but XP only sees the linux shares, not the actual machine name. 

any suggestions or is this impossible? thanks

also can i even do this or do i have to create a domain for it thanks again

---

### Post by Iowan on 2009-07-31
**Winbind** comes to mind, but I'm trying to remember which direction (win->linux or linux->win) it helps...

---

### Post by evilbuntu on 2009-07-31
> **Iowan said:**
> **Winbind** comes to mind, but I'm trying to remember which direction (win->linux or linux->win) it helps...

winbind would be more a domain thing than a workgroup thing though correct?
i really only have the two computers i am worried about seeing each other.

---

### Post by lykwydchykyn on 2009-07-31
> **evilbuntu said:**
> winbind would be more a domain thing than a workgroup thing though correct?
i really only have the two computers i am worried about seeing each other.

Correct, winbind is for joining the Samba machine to a domain.  Not applicable here.

Can you post your /etc/samba/smb.conf file?  Also, are you running a firewall on the Ubuntu machine?  Netbios name resolution uses a different port than the actual SMB file sharing, IIRC; so it's possible for one to be filtered but not the other.

---

### Post by evilbuntu on 2009-08-01
no firewall on ubuntu at the moment due to my samba problems. windows firewall on XP. i use webmin to manage my samba stuff. here is my config file


[global]
	load printers = yes
	name resolve order = bcast host lmhosts wins
	usershare owner only = False
	username map = /etc/samba/user.map
	map to guest = Bad User
	encrypt passwords = true
	use client driver = yes
	printcap cache time = 750
	netbios name = "its my workgroup name" 
	cups options = raw
	usershare max shares = 100
	printing = cups
	server string = 
	path = /media/SimpleDrive/ProFTP
	local master = yes
	workgroup = "my workgroup name"
	os level = 65
	printcap name = cups
	usershare allow guests = Yes

[printers]
comment = All Printers
path = /var/spool/samba
printable = Yes
create mask = 0700
guest ok = Yes
browseable = No

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
read only = Yes
guest ok = No

[stuff]



as i said i can see my default shared drive but not the actual machine in XP
thanks

---

### Post by evilbuntu on 2009-08-03
well figured it out, so now my xp actually "sees" my ubuntu machine in the workgroup. from my windows machine i can get into the ubuntu machine and "see" the linux users but unfortunately when i want to go to my admin groups in my xp  machine it only want to find users on itself not other machines in the workgroup

---

