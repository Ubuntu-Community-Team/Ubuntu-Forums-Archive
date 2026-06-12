---
title: "[SOLVED] Samba - Sharing external USB drive not working"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by skern03 on 2008-12-24
I'm running U8.04 and I've set up Samba and Winbind. I have shares on internal drives that are visible and function perfectly on two Win XP machines on my network. However, two shares on my external USB attached hard drive do not function. They appear, but Windoze generates an error message: "The network path was not found." See attached image.

I configured Samba using system_config_samba (which works great, BTW!!). I have share access turned on, and an internal workgroup specified. I've reviewed the settings in smb.conf, and I can't see any obvious errors or differences between the internal and external hard drive shares.

Here's the output of sudo testparm -s /etc/samba/smb.conf. I do get one error before the output streams in the terminal window, "unable to resolve host" followed by my machine name.

> Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Backups]"
Processing section "[Installs]"
Processing section "[StevesMusic]"
Processing section "[StevesSharedDocs]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
	workgroup = KERN
	server string = %h server (Samba, Ubuntu)
	security = SHARE
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
	invalid users = root

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Backups]
	comment = External drive - backup folders
	path = /media/BACKUP_DRIV/Backups
	read only = No
	guest ok = Yes

[Installs]
	comment = External drive - installation files
	path = /media/BACKUP_DRIV/Installs
	read only = No
	guest ok = Yes

[StevesMusic]
	comment = Internal drive - Steve's shared music
	path = /media/Beast_drv/Documents and Settings/All Users/Documents/My Music
	read only = No
	guest ok = Yes

[StevesSharedDocs]
	comment = Internal drive - Steve's Shared Documents
	path = /media/Beast_drv/Documents and Settings/All Users/Documents
	read only = No
	guest ok = Yes


Any ideas what I'm doing wrong?

---

### Post by skern03 on 2008-12-26
BUMP...

New info... if I open Network, then open my machine from the list and click one of the shares on the external USB hard drive, I get the following error: 
    Unable to mount location.
    Failed to mount Windows share.
See attached.

The other shares on the internal disk drives open with no issues.

---

### Post by superprash2003 on 2008-12-26
try Read Only = Yes..


[sharename] comment = Any comment you like
 path = /media/drive
 public = yes 
writable = yes 
create mask = 0777 
directory mask = 0777
 force user = nobody 
force group = nogroup

---

### Post by skern03 on 2008-12-27
Tried that, and tried the way you have the share set up in the quote. No luck. I also did a complete reinstall to a new drive. Still no luck. I'm stumped. Everything looks like it ought to work, yet it doesn't.

Thanks!

> **superprash2003 said:**
> try Read Only = Yes..


[sharename] comment = Any comment you like
 path = /media/drive
 public = yes 
writable = yes 
create mask = 0777 
directory mask = 0777
 force user = nobody 
force group = nogroup

---

### Post by JBetts on 2008-12-27
Wow, I was having the exact same issue like ONE page over in the forums...! [http://ubuntuforums.org/showthread.php?t=1023084](http://ubuntuforums.org/showthread.php?t=1023084)

Right after I posted that, I apparently found a solution! I changed three things, and I'm not sure which solved my problem. My current smb.conf (the pertinent part):

[External]

comment = stuff
path = /media/JBetts HDD/Archive
writeable = no
browseable = yes
guest ok = yes

1) I changed path = *from* /media/JBetts\ HDD/Archive 
Maybe path doesn't accept escapes? 
2) I added the writeable = no. 
Maybe this has to be dictated yes or no, as its an external drive? 
3) I checked the "Enable write support for external device" on the NTFS configuration tool (I think accompanied with the ntfs-3g driver). 
Maybe basic write access was keeping me from opening the path? 


It is strange, because my scenario was *verbatim* like yours - able to access locally, with the same error messages. 

Hope that helps!

---

### Post by skern03 on 2008-12-28
Thanks for the suggestions. 

I tried matching your smb.conf with no luck. The path already has no spaces:
	path = /media/BACKUP_DRIV/Backups
And I tried changing writeable and browseable as you suggest, again, no effect.

As for NTFS tools, this drive is FAT32 - I set it up that way some time ago when Linux support for NTFS was flaky. At least, that's my recollection ;-).

I wonder... maybe I should copy the external backup drive and reformat as NTFS and see if that works. Or perhaps set up an NTFS partition on the external drive...

> **JBetts said:**
> Wow, I was having the exact same issue like ONE page over in the forums...! [http://ubuntuforums.org/showthread.php?t=1023084](http://ubuntuforums.org/showthread.php?t=1023084)

Right after I posted that, I apparently found a solution! I changed three things, and I'm not sure which solved my problem. My current smb.conf (the pertinent part):

[External]

comment = stuff
path = /media/JBetts HDD/Archive
writeable = no
browseable = yes
guest ok = yes

1) I changed path = *from* /media/JBetts\ HDD/Archive 
Maybe path doesn't accept escapes? 
2) I added the writeable = no. 
Maybe this has to be dictated yes or no, as its an external drive? 
3) I checked the "Enable write support for external device" on the NTFS configuration tool (I think accompanied with the ntfs-3g driver). 
Maybe basic write access was keeping me from opening the path? 


It is strange, because my scenario was *verbatim* like yours - able to access locally, with the same error messages. 

Hope that helps!

---

### Post by JBetts on 2008-12-28
I also started using Samba Server Configuration tool (1.2.63). I don't know if that was just coincidence or luck.

Personally, I wouldn't recommend reformatting into NTFS if you don't need to, as linux doesn't really play nice with other ubiquitous formats. 

Like I said, I like GUIs (coming from Windows) and the config tool makes Samba a LOT easier...and I think just changes the smb.conf to reflect what you're doing in the GUI. 

That said, if our coincidentally similar problem wasn't fixed by any of those three things, give the config tool a try.

---

### Post by skern03 on 2008-12-28
> **JBetts said:**
> I also started using Samba Server Configuration tool (1.2.63).

As mentioned in my first post, I'm already using the Samba config tool, and unfortunately, didn't get the results you did.

> Personally, I wouldn't recommend reformatting into NTFS if you don't need to, as linux doesn't really play nice with other ubiquitous formats.

Over the past two years, Linux has improved dramatically. I can now set up a permanent login to my windows drive (I like to keep the two OS's as far apart as physically possible :P) from Linux the first time I log onto it.

What I plan to do is format a small partition just to see if it works. If it does, then I'll do the entire USB drive. Otherwise, I'll just kill the partition.

What I'd really like to set up is a network attached storage device for backups and shared files like music and pictures. But I've read those have issues as well.

Thanks for your suggestions!

---

### Post by skern03 on 2008-12-28
> What I plan to do is format a small partition [as NTFS] just to see if it works.

And THAT worked! Here are the steps I took:
[LIST=1]
[*]Plugged the USB drive into a windows machine w/Partition Magic loaded  (GParted from the Live CD puked).
[*]Using Partition Magic, I resized the FAT32 partition, leaving about 10 GB. 
[*]Formatted the 10 GB partition as NTFS.
[*]Clicked the Safely Remove Hardware icon in the windows system tray, and selected the USB drive for removal.
[*]Plugged the USB drive back into my Ubuntu 8.04 machine. The new 10 GB partition appeared in my list of places. 
[*]Opened it, and dragged a folder into it.
[*]Shared the new folder using the Samba Server Config utitlity.
[*]Opened it through Network Places on the Ubuntu machine. It worked!!!
[*]Opened it on a Windows machine attached to my network. That worked too!!!
[/LIST]

So in short, the issue was that Ubuntu Samba networking doesn't recognize external drives formatted as FAT32. 

Now I plan to convert the drive to NTFS.

---

### Post by JBetts on 2008-12-31
Crazy! 

Well, congrats man! That's good info to have...especially to those running multiple OS environments! 

I guess it was just dumb luck that my external was already formatted to NTFS. Now if I can just get it auto-syncing with my ext3 partition...

Congrats again!

---

### Post by grossinm on 2009-01-05
> **skern03 said:**
>  So in short, the issue was that Ubuntu Samba networking doesn't recognize external drives formatted as FAT32. 

Now I plan to convert the drive to NTFS.

I have the same situation, but the drive is NTFS and still cannot write to the drive.

See this bug report, sounds similar, but its marked as fixed:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/224317](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/224317)

---

### Post by skern03 on 2009-01-06
> **grossinm said:**
> I have the same situation, but the drive is NTFS and still cannot write to the drive.

See this bug report, sounds similar, but its marked as fixed:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/224317](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/224317)

I assume you've checked smb.conf, and verified that the share has write permissions, so I would post a bug report anyway. I did same thing with another bug marked fixed, altho I was later told it was marked fixed for one version of Ubuntu, but still had an open task for the version I was then using. They merged it with the original bug report. Not sure if it does much good, but it can't hurt.

BTW, write permissions work fine on my newly converted NTFS drive.

---

### Post by rafemonkey on 2009-02-04
Just to add a little confusion...

I was having a similar problem sharing a USB drive, I stumbled on this thread, and was able to fix my problem. In my case I was trying to escape the space in the file name, which was messing things up...

This
```
path = /media/My\ Book
```
failed, but when I took out the escaped space, it worked fine...

Anyway, here's my working share..
```

[backup]
        comment = Network Backup
        read only = no
        path = /media/My Book
        guest ok = yes

```
The (kinda) interesting thing is that my drive is not formatted NTFS, rather it's VFAT. Maybe it's a issue with FAT32? Or maybe it's something with the configuration tools? Since I don't need anything fancy, I just tacked my stuff onto the end of the vanilla smb.conf using a text editor.

Thanks for setting me on the right path!

---

### Post by skern03 on 2009-02-04
> **rafemonkey said:**
> Just to add a little confusion...

The (kinda) interesting thing is that my drive is not formatted NTFS, rather it's VFAT. Maybe it's a issue with FAT32? Or maybe it's something with the configuration tools? Since I don't need anything fancy, I just tacked my stuff onto the end of the vanilla smb.conf using a text editor.

Thanks for setting me on the right path!

Together, we can muddle through almost anything! BTW, it's definitely an issue w/FAT32 on an external USB HD.

---

### Post by diosif on 2010-08-29
Well, the problem I have is related but not exactly the same. My USB shares work perfectly, until i restart the server. Then they are lost and I have to re-share them. But I share them through gksu Nautilus. Do you thing that my problem will be solved by declaring my shares (even USB) in smb.conf?

---

### Post by Morbius1 on 2010-08-29
Just so you know, there is a bug related to how Nautilus shows the shared folder and how it reports the share. It's probably still shared. Here's the only reliable way to find out:

Issue the following command from a terminal:
```
net usershare info
```[COLOR=Blue]EDIT: didn't realize you were using "gksu nautilus"[/COLOR]
Your command would be:
```
 sudo net usershare info
```

---

