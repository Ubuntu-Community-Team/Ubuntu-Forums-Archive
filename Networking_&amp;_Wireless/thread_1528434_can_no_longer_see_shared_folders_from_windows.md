---
title: "can no longer see shared folders from windows"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by ZenMasta on 2010-07-10
I have an old 7.04 box that I used to use for file sharing. I set this up a long time ago and it used to work perfectly. I was able to see 2 shared folders from windows and I could drag and drop etc. 

Well, I recently reformatted my windows computer and attempted to connect to the ubuntu network shares... but I cannot. 

From windows if I try to view \\ubuntu it prompts for username and password... when I do that all I see is "Printers and Faxes"

Basically the only thing that changed besides me reformatting my windows computer was the workgroup name, but I already fixed that in ubuntu.

if I remote into the ubuntu computer and double click the network servers icon on the desktop I see, UBUNTU, Windows Network, WINDOWS. If I double click Windows Network I'll see my workgroup name, and if I double click that, then I see only the 2 computers. If I try to drill down further on either of the computers I don't see any folders.

Here is my samba config
> # Samba config file created using SWAT
# from 68.183.230.10 (68.183.230.10)
# Date: 2008/04/04 15:39:04

[global]
	workgroup = zenny
	server string = samba
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

wins support = no
[printers]
	comment = All Printers
	path = /tmp
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[pics]
	writable = no
	public = no
	browsable = no
	path = /home/zen/pics


available = no
[docs]
	writable = no
	public = no
	browsable = no
	path = /home/zen/docs




available = no


---

### Post by Morbius1 on 2010-07-10
> [pics]
    writable = no
    public = no
[COLOR=Blue]     browsable = no[/COLOR]
    path = /home/zen/pics
[COLOR=DarkRed]available = no[/COLOR]> [docs]
    writable = no
    public = no
[COLOR=Blue]     browsable = no[/COLOR]
    path = /home/zen/docs
[COLOR=DarkRed]available = no[/COLOR]                      bowsable = no will render your shares invisible to the network. Change it to yes or delete the line.

available = no basically renders the share inactive. Change it to yes or delete the line.

With these two changes you'll at least see the shares. Nobody without a samba password will be able to access them but they will be able to see them.

---

### Post by ZenMasta on 2010-07-10
Thanks Morbius that was simple enough. I guess maybe I changed it or something although I don't remember doing so. This also answers an old question I had... in the past I couldn't see the shared folders but I could definitely access them if I knew the path. the browseable = no answered that question.

Thanks again.

---

