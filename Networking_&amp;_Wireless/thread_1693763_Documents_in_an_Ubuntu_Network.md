---
title: "Documents in an Ubuntu Network"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by biyuya on 2011-02-23
I have 6 Ubuntu 10.10 machines in a netwok saharing documents. Every time I open a document from a different machine than the origin of  the document, I must open a copy of the document to edit it. Is it a way to avoid that?

Thanks a lot

---

### Post by Kirboosy on 2011-02-23
How exactly are you sharing the document? 

If you don't have the write permissions enabled the remote users can't edit the files and save to the same location.

---

### Post by biyuya on 2011-02-23
Where I must enable the write permissions? Sorry but I am new in the area Ubuntu networking.

Thanks

---

### Post by Kirboosy on 2011-02-23
On the Folder (directory, whatever you want to call it) right click and select "Sharing Options"

Then make sure the "Allow others to create and delete files in this folder" is checked.

---

### Post by biyuya on 2011-02-23
Thats the way the folders are configured.

Thank you.

---

### Post by Kirboosy on 2011-02-23
Ok lets try this...

1. Unshare the folder

2. Open Synaptic (System-->Admin-->Synaptic) 

3. In the quick  search box type "system-config-samba"

4. Check the package that matches...

5. Open the new tool under System-->Admin-->Samba Configuration

6. Add the directory (you can even select a whole drive)  that you wish to share and set the permisions for everyone to access read and write.


See if that changes anything

---

### Post by Morbius1 on 2011-02-23
> Every time I open a document from a different machine than the origin of the document, I must open a copy of the document to edit itIf you are using nautilus-share and you have a guest share then eveytime a remote user saves something to your share it will save as owner = nobody. You can't write to it because you aren't "nobody"

To fix this ( for nautilus-share ):
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to your [global] section:
```
force user = your-user-name
```[COLOR=Blue]*Change your-user-name to you actual local login user name*[/COLOR]
Save smb.conf and back in the terminal restart samba:
```
sudo service smbd restart
```If your using classic-share (System-->Admin-->Samba Configuration ) it gets more complicated.

If you don't know which samba method you're using post the output of the following comands:
```
net usershare info --long
``````
testparm -s
```

---

### Post by biyuya on 2011-02-23
Morbius1:

Here is the information you requested:


emi@emi-Satellite-A80:~$ net usershare info --long
[público]
path=/home/emi/Público
comment=Archivos compartidos
usershare_acl=Everyone:F,
guest_ok=y

emi@emi-Satellite-A80:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
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

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
emi@emi-Satellite-A80:~$

---

### Post by Morbius1 on 2011-02-24
You have one share:
> [público]
path=/home/emi/Público
comment=Archivos compartidos
usershare_acl=Everyone:F,
guest_ok=yIt's a nautilus-share , what Samba calls a Usershare, so to make it so user "emi" can edit the files:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf 
```Add the following line to your [global] section:
```
  force user = emi 
``` Save smb.conf and back in the terminal restart samba:
```
  sudo service smbd restart
```

Every new file added by a remote user will save as "emi" as owner.

---

### Post by biyuya on 2011-02-25
I made the change, but dosn't work

---

### Post by Morbius1 on 2011-02-25
What doesn't work?

(1) A file added to Público doesn't have emi as the owner?

(2) Or the files you already had in /home/emi/Público haven't changed?

The old files won't change until you change their ownership to you:
```
chown -R emi /home/emi/Público
```

All new files will save with emi as owner.

---

