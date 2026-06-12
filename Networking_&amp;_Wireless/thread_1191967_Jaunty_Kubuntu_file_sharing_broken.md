---
title: "Jaunty Kubuntu file sharing broken"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by robertsaron on 2009-06-19
There are 3 computers in the house. 2 have kubuntu the latest release. The 3rd has windows vista 64 bit ultimate edition.

Both linux boxes can see the file shares on vista. Vista cannot see the shares on either linux box. The linux box cannot see the file shares on each other. 

Any ideas or sugestions? Unable to post the SMB.conf or what ever it is, as I am at work can do later if needed. I can also post a pic of the physical network lay out if needed.

---

### Post by SpeedyxDevil on 2009-06-19
I have problems too (that stay unanswered but nvmd).
I got Kubuntu on my laptop and vista ultimate on my dekstop.
I used to be able to browse the desktops files but now on kubuntu when I want to go to my desktop it asks me the user and password but even if I type in the correct user and password, it keeps asking me that, every KDE based pc in the house has the same problem.
I can't think of any changes accept automatic updates on vista that could've caused this. How did you manage to view your shares on vista from your kubuntu?

---

### Post by swerdna on 2009-06-19
> **robertsaron said:**
> There are 3 computers in the house. 2 have kubuntu the latest release. The 3rd has windows vista 64 bit ultimate edition.

Both linux boxes can see the file shares on vista. Vista cannot see the shares on either linux box. The linux box cannot see the file shares on each other. 

Any ideas or sugestions? Unable to post the SMB.conf or what ever it is, as I am at work can do later if needed. I can also post a pic of the physical network lay out if needed.

You can create a diagnostic version of smb.conf for each Linux box. Open a Gnome terminal and enter this command:```
testparm /etc/samba/smb.conf > /home/lulubelle/Desktop/samba.txt
```Do that for each Linux box. replace "lulubelle" with your username.

That will create a text file with a cut-down diagnostic version of smb.conf on your desktop for each Linux box. Copy/paste the contents here and we'll see if we can see the problem.

---

### Post by robertsaron on 2009-06-20
Here is the dump file. I guess I must have had a partial install of samba. Just smb was installed. I installed samba, now my vista box can see the linux one i want it to. Just the printers though. it cannot see the drive with all the media on it.

The computer that needs to be shared out has 2 drives. Drive 1 is for the OS. Drive 2 is for all my movies and music etc. This is the livingroom computer. My vista box is in my bedroom. That is my gamingcomputer.

[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
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

---

### Post by robertsaron on 2009-06-20
> **SpeedyxDevil said:**
> I have problems too (that stay unanswered but nvmd).
I got Kubuntu on my laptop and vista ultimate on my dekstop.
I used to be able to browse the desktops files but now on kubuntu when I want to go to my desktop it asks me the user and password but even if I type in the correct user and password, it keeps asking me that, every KDE based pc in the house has the same problem.
I can't think of any changes accept automatic updates on vista that could've caused this. How did you manage to view your shares on vista from your kubuntu?
Speedyxdevil

It was a lot of tinkering. I will send you steps as soon as I remember. It took me a few days to figure out. This was done on Vista ultimate 64 bit. What version of vista do you have ? that might make a HUGE difference.

---

### Post by swerdna on 2009-06-20
Here's how to share out drive 2. The partition on the drive that contains all the media that you want to share will be called something like sdb1 and it will be mounted somewhere, for discussion purposes suppose it's mounted in directory abcde located at /path_to/abcde

You can find out what sdb1 actually is from the return you get to this Gnome terminal command:```
sudo fdisk -l
```
You can find out what /path_to/abcde is from the return you get to this terminal command:```
df -Th
```

If you can't deduce what your version of sdb1 and/or /path_to/abcde is, then just post the returns back here and we'll check it out.

Then put a [stanza] in your file smb.conf to share the media. You can open smb.conf (a text file) for editing in the "gedit" GUI editor with this command in a terminal window: ```
gksudo gedit /etc/samba/smb.conf
```

Put this stanza at the bottom:
```
[media]
path = /path_to/abcde
guest ok = yes
read only = yes
```

restart Samba with this console command:```
sudo /etc/init.d/samba restart
```
Restart vista computer.
That should make the media available for read-only viewing and copying of the media files.

---

### Post by robertsaron on 2009-06-20
All thanks for the help, I figured out how to do it shortly before you posted lol. To the person who was asking about vista file sharing, this was done on Vista Ultimate:

One of the things that lots of people have asked me is how to share files between 2 different computers. Most households now have more than 1 computer, and want seamless transfer of files back and forth, with out using portable drives. This is possible with XP and Vista, though these steps only cover enabling file sharing on Vista Ultimate to communicate to a Linux box. Though in theory, it should allow Xp to see the files on Vista.

1. Right click on the drive or folder that you want to be shared
2. go to properties - sharing tab
3. click on advanced sharing
4. check the box that says share this folder
5. Down below click on permissions
6. click on everyone
7. Below there will be 3 check boxes; full control, change and read, 8. Place a check in each box
9. click apply then ok
10. Keep clicking on apply then ok (if needed) on all screens until  back to the main screen

In Control panel, under programs and features, on the left click Turn windows features on or off. Place a check in services for NFS and Subsystem for UNIX-based Applications. Click on ok, wait for windows to install, then it is finished. I hope this helps everyone out. Vista has some built in Active directory stuff. Which is basically built off of LDAP. It is M$ version of LDAP.

---

