---
title: "force file permission from windows 7 clients via samba using SWAT on 10.04 LTS"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by jabrown65 on 2011-06-11
It seems to me this should be pretty basic, but none of the instructions Ive followed have made the slightest difference.

On a home network we have a particular shared folder on a ubuntu 10.04LTS server which we want all users to always have full read write execute access to every file and folder regardless of who creates the file or on what computer they create it, including a couple of Windows 7 laptops.

However, no matter what I have tried, at the moment whenever a file is created using one of the Windows 7 laptops it has user access only. 

e.g. what I am getting is:

-rwxr--r-- xx  thisusergroup thisusername ... thisfilename

what I want is for all users to write files with permissions:

-rwxrwxr-- xx  ourusergroup dontcarewhichuser ... thisfilename

or even:

-rwxrwxrwx xx   dontcarewhichgroup  dontcarewhichuser ... thisfilename


How do I achieve this?? ... preferably using SWAT

---

### Post by Morbius1 on 2011-06-11
You have a default user on your Linux server named "nobody" with group "nogroup". One way around your dilemma is not to force permissions but to force ownership of the saved file. 

Add the following line to the share definition:
```
force user = nobody
```Each new file will save with 644 permissions but the owner will be nobody and all remote users will be converted to nobody after authentication ( if this is not a guest share ).

---

### Post by jabrown65 on 2011-06-12
Thanks for your reply. That is the kind of thing I've been trying, but to no avail.

When I changed the following to user 'nobody' then literally nobody is able to access it, unforunately!

drw-rw-r--  6 nobody jbcp        4096 2010-09-06 20:44 Communic

See the /media/data share in my smb.conf below:


# Samba config file created using SWAT
# from UNKNOWN (127.0.0.1)
# Date: 2011/06/12 14:10:17

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
	usershare owner only = No
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

[FS-1010]
	comment = Kyocera FS-1010
	path = /var/spool/samba
	read only = No
	create mask = 0700
	guest ok = Yes
	hosts allow = 10.0.0.0/255.255.255.0
	printable = Yes
	printer name = FS-1010
	oplocks = No
	share modes = No

[/media/data]
	force user = nobody
	read only = No
	create mask = 0777
	guest ok = Yes
	available = No
[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No


Further suggestions?

John

---

### Post by Morbius1 on 2011-06-12
There are are a whole bunch of things wrong with your share definition:
> [/media/data]
    force user = nobody
    read only = No
    create mask = 0777
    guest ok = Yes
    available = No* You have no path defined so the share goes nowhere.
* You have the share flagged as unavailable so the share will be ... well ... unavailable.
* You are allowing write access to guests but the Linux permissions on the target directory won't allow it.

I would do the following:

* Change the share definition to this:
> [**[COLOR=Blue]media-data[/COLOR]**]
     force user = nobody
**[COLOR=Blue]path = /media/data[/COLOR]**
     read only = No
     create mask = 0777
     guest ok = Yes
     **[COLOR=Blue]available = Yes[/COLOR]*** Then to insure that a remote guest can actually enter the share and so that "nobody" can actually add to the target folder:
```
sudo chmod 777 /media/data
```I'm assumming that /media/data in this exercise is pointing to a linux formatted partition or directory. If it's pointing to an NTFS or Fat32 partition then we need to talk further.

---

### Post by jabrown65 on 2011-06-14
Thanks. That worked. I am not sure why SWAT got it so wrong in th first place???

After making the changes, restarting smbd and nmbd services was insufficient. I had to restart the server for the share to start working as desired. Note I noticed that I'd also attempted to share the folder using the "Create Share" menu item, which also hadn't work. I disabled that before restarting the server, but I am not sure if that was a factor in the share starting to work as desired.

---

### Post by Morbius1 on 2011-06-14
SWAT is a destructive utility in that it doesn't modify the original smb.conf it creates it's own. Some distros actually remove SWAT from their repository. Add to that the fact that swat hasn't been maintained since the Eisenhower administration ( that might be a slight exaggeration ;) ) it's a miracle you got as far as you did.

---

