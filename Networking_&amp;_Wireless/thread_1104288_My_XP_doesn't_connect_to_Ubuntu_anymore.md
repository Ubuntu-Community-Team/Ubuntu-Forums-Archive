---
title: "My XP doesn't connect to Ubuntu anymore"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by ogger on 2009-03-23
I am not sure what I screwed up, but I am very new here and while I am installing things over the last couple of weeks on my new Ubuntu machine, I must have disconnected the two. 

I still can see Ubuntu in Mshome under my networkplaces, but when I click on it it says \\Peter is not accessible ....

Also, when I go to the Windows command line and type \\192.168.1.5 it says "The network patch was not found."

Here is my Samba configuration. I am playing around with this since a couple of weeks.

```
[global] 
	workgroup = Mshome 
	netbios name = Peter 
	server string = Peter Server2 (Samba, Ubuntu) 
        security = user
        encrypt passwords = true
        map to guest = bad user
        guest account = nobody
	wins support = yes
[homes] 
	comment = Home Directories 
	browseable = yes 
	writable = yes	 
[public]
        comment = Public Share
        path = /home/peter
        read only = no
        guest only = yes
        guest ok = yes
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

I also tried using 'sudo smbpasswd -a username' as suggested in the Ubuntu Documentation, but it didn't help.

---

