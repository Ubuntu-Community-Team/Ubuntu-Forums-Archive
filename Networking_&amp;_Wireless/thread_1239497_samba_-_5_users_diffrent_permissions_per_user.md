---
title: "samba - 5 users diffrent permissions per user"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by vladilinsky on 2009-08-13
I have been trying for days now to get this setup working

The setup is, a folder (files) is shared and it has different sub dirs (drawing, sales, signs, reception) in it.
the first sub folder (drawing) must be read-able by all users but only writable by 2 (peter and drawing)
the second sub folder is the same but different users (peter and sales)
so basically (peter) should be able to read write everything and all users only write to there specific folder but be capable of reading all folders.  

I have the local permissions working correctly (when i log directly to the ubuntu file server everything works). but over the network no one can write anything anywhere. 
 
Any help would be greatly appreciated.
I am attaching both my smb.conf and my smbusers files

*************************

smbusers

 # Unix_name = SMB_Name1 SMB_Name2 ...
root = peter
nobody = guest smbguest pcguest
reception = reception
drawing = drawing
signs = signs
sales = sales

*************************

smb.conf

[global]

workgroup = WORKGROUP

	server string = %h server (Samba, Ubuntu)
	dns proxy = no
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
####### Authentication #######
   security = user
	encrypt passwords = true
	passdb backend = tdbsam
	obey pam restrictions = yes
	unix password sync = yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .


	pam password change = yes
	map to guest = bad user


[printers]
	comment = All Printers
	browseable = no
	path = /var/spool/samba
	printable = yes
;	guest ok = no
;	read only = yes
	create mask = 0700


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = no


[files]
	path = /files
	writeable = yes
	browseable = yes
	public = yes
	valid users = drawing reception server peter sales signs
	write list = drawing reception server peter sales signs	
	force create mode = 0660
        force directory mode = 0770

---

### Post by swerdna on 2009-08-14
You can't have "public = yes" in a share that requires authentication; "public = yes" is a synonym for "guest ok = yes", and guests are incompatible with "valid users".

---

### Post by vladilinsky on 2009-08-14
Thanks that explained some things.  

In the end I have rearranged the dir structure for a simpler smb.conf file.   now each user has their own dir at file level and can view others files but not edit. no single user can view and edit everything.

---

### Post by AfrikaDietmar on 2010-06-07
Hi vladilinsky, i'm trying to do something similar like you did, do you mind giving some details how you gave those permissions to different folders, or what did you add or change in your smb.conf to get those folders which each user can access whereby only edit their own folder ?

---

