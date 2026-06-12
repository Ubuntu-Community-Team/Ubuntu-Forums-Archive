---
title: "Sharing files Ubuntu Win7"
date: 2011-02-15
forum: Networking &amp; Wireless
---

### Post by gilch on 2011-02-15
I have had Ubuntu on my desktop and Windows 7 on my laptop for a couple of years.

Ubuntu machine is hard wired to the router, and the laptop is wireless.

I have access to internet with no problem from both machines.

I have always desired to share files between computers. It is very frustrating to always have to use a CD or DVD to share files. Everytime I look at networking I get lost and I give up. I looked again tonight and I still am afraid to venture in setting that up. 

Is there an EASY way? I have had Ubuntu (now 10) for two years but I have not learned much at all. Just used it as a computer, period.

I need someone to hold my hand...

---

### Post by pricetech on 2011-02-15
Try this:

[http://ubuntuforums.org/showthread.php?t=1644585](http://ubuntuforums.org/showthread.php?t=1644585)

---

### Post by gilch on 2011-02-16
Thanks. I tried that, everything went well until
System - Administration - Samba

Samba was not present under Administration???

---

### Post by pricetech on 2011-02-18
Did you install "system-config-samba" using Synaptic ???  That should make it appear.

---

### Post by aeiah on 2011-02-18
if you're more interested in just file transfer rather than file sharing (ie, just occasionally you want to move files from one computer to the other etc) then you could just go with ssh/winscp if samba is proving problematic.

the advantage of samba of course is that the network location is treated as local, so you can access it all conveniently when its set up.

---

### Post by gilch on 2011-02-18
I want to move files from one computer to the other from either computer.
I tried to configure Samba but I am not getting anywhere.
I think I created a user - the name of my laptop. but then I have to handle Server Settings.  What do I do with ... %h server (Samba, Ubuntu) ... ???

---

### Post by Morbius1 on 2011-02-18
> I tried to configure Samba but I am not getting anywhere.
I think I created a user - the name of my laptop. but then I have to  handle Server Settings.  What do I do with ... %h server (Samba, Ubuntu)  ... ???Let's find out what method of Samba you are using ( there are 2 ) and how you are using it. Please post the output of the following commands:
```
testparm -s
``````
net usershare info --long
```

---

### Post by gilch on 2011-02-18
Thanks.
Here goes...

gilles@gilles-desktop:~$ testparm -s
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
	username map = /etc/samba/smbusers
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
gilles@gilles-desktop:~$ 


When I entered net usershare info --long,
nothing happenednet user

gilles@gilles-desktop:~$ net usershare info --long
gilles@gilles-desktop:~$

---

### Post by Morbius1 on 2011-02-18
Well you have a pristine copy of smb.conf and you have no shares defined so let's do Samba the easiest way:

Open Nautilus
Right click a folder you own say ... Documents
Select "Sharing Options"
[COLOR=Blue]*At this point if you don't have Samba installed it will ask you if you want to install it - you do.*[/COLOR]
Select "Share this folder", "Allow others to create and delete..", "Guest Access".
Select "Create Share"
It will ask you if you want it to modify permissions - you do.
Done

No need to restart any services.
No need to create any samba users or passwords.

To verify that a share has been created:
```
net usershare info --long
```To verify if someone on the network can see it:
```
smbtree
```That should list all the workgroups on your LAN and all the hosts on those workgroups and all the shares on those hosts.  All we're interested at the moment is if the system can see it's own samba shares.

---

### Post by gilch on 2011-02-18
I don't know if I have Nautilus or not, but when I right click the folder Documents (for example) I cannot see any option for sharing.

(I cannot continue right now, since I have to go out until late tonight.
I will continue then.)

---

### Post by Morbius1 on 2011-02-18
Then you are either not using Ubuntu ( Gnome ) or you have the following package missing:
```
sudo apt-get install nautilus-share
```

---

### Post by Morbius1 on 2011-02-18
If you are not using Gnome then you can also use System > Administration > Samba

To create the equivalent of the above nautilus-share and assuming your login name is gilch:

_BASIC TAB_
Directory: /home/gilch/Documents
Share Name: documents
Select "Writable" and Visible"

_ACCESS TAB_
Select "Allow access to everyone"

Select OK.

You need to do one more thing to avoid an access error from the remote machine and that's to change permissions on the target folder:
```
sudo chmod 0777 /home/gilch/Documents
```Then run the following command to see if you can see your own shares:
```
smbtree
```

---

### Post by gilch on 2011-02-19
I finally found Share under Properties. Ill see if that works from the other machine.

---

### Post by gilch on 2011-02-19
I did find Share under Properties. I did what it asked.

What now? I can't see those files from my Win7 machine, and I cannot see my Win7 machine from Ubuntu.  Not much advanced yet. (Please don't give up on me ! ! !)

Gilles

---

### Post by Morbius1 on 2011-02-19
From Ubuntu post the output of the following command:
```
smbtree
```

---

### Post by gilch on 2011-02-20
I have made some progress. I can see folders on Win7 from Ubuntu, but some of them are still saying access denied.
Here is smbtree

gilles@gilles-desktop:~$ smbtree
Enter gilles's password: 
WORKGROUP
	\\GILLES-VAIO    		Gilles-VAIO
	\\GILLES-DESKTOP 		gilles-desktop server (Samba, Ubuntu)
		\\GILLES-DESKTOP\pictures       	
		\\GILLES-DESKTOP\new volume     	
		\\GILLES-DESKTOP\music          	
		\\GILLES-DESKTOP\Photosmart-C6200-series	HP Photosmart C6200 series
		\\GILLES-DESKTOP\print$         	Printer Drivers
		\\GILLES-DESKTOP\IPC$           	IPC Service (gilles-desk


When I go to do the chmod,
I don't know how to refer to the files 
\\GILLES-DESKTOP\new volume
and 
\\GILLES-DESKTOP\music 

These are on different hard disks.
If I go to Places, I find these files under
media
then
file system
then
new volume

How do I refer to that in the chmod command?

---

### Post by gilch on 2011-02-20
OK I have figured it out. I was forgetting about the use of Capital letters. Once I wrote it as follows it worked:

sudo chmod 0777 /media/"New Volume"/

THANK YOU ALL,

I now see my Ubuntu files from Win7.

One last hurdle:

when I try to see files from Win7 on the Ubuntu desktop, it says
Unable to mount...

I;ll be out of your hair after this one. I promise.

---

