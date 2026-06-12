---
title: "File Sharing Problem between two Dapper machines"
date: 2006-05-01
forum: Networking &amp; Wireless
---

### Post by Jose Catre-Vandis on 2006-05-01
File Sharing Problem - Am I nearly there?  [edit - sorry, just realise this hit a hardware help section :-D]

I have two up to date Dapper machines on a LAN, lets call one Bill and the other Ben

Bill is a file server, with two hard drives
Bill has samba running
Bill has an IP of 10.10.10.65
Logged into Bill with username=John and password=smith
Bill has a directory called /Music with lots of music on it
/Music is owned by group lanusers, of which John is a member and all files are 0777
/Music is a shared folder under Samba and on the second hard drive, and had to be mounted in fstab
/Music is a linux ext3 folder/drive
smbusers contains John = "network_username" and the password has been setup.
Bill has a fat32 partition called /Share

Ben is a workstation with one hard drive
Ben has Samba running
Ben has an IP of 10.10.10.60 
Logged into Ben as username=Tom and password=Jones
Can browse 10.10.10.65/Music via browser using smb://
Successfully setup a share to /Music from Ben using:
```
sudo mount //10.10.10.65/Music /media/svrmusic/ -o username=John,password=Smith,dmask=777,fmask=777
```
(not yet set up a boot up link in fstab)
gets a nice drive icon for svrmusic on desktop and can browse using nautilus as Tom but read only
Tom, working on Ben, only has read only access to /Music on Bill, and Tom would like to be able to have read/write access.
Tom can read/write /Share on Bill
As root on Ben, still can only read only


**What has Tom missed in setting up /Music as read/write ?**

---

### Post by Jose Catre-Vandis on 2006-05-02
bump

Oh, come on, someone must know the answer, please.

---

### Post by Iowan on 2006-05-02
How is /Music shared on Bill? (What's in the smb.cfg?)
> Tom can read/write /Share on Bill
Tom is a Linux/Samba user on Bill?
Is Tom a member of lanusers?
What's John doing while Tom is having all the fun? ;)

---

### Post by Jose Catre-Vandis on 2006-05-02
Tom is a samba user on Bill
Tom is a member of lanusers

but

you have pointed me to the right place :-D

In my smb.conf I find
```
[Music]
path = /Music
available = yes
browseable = yes
public = yes
writable = no
```

I edited writeable to yes, and I can now do what I wanted, so many many thanks for the pointer. :-D Why oh why doesn't smb sharing in Gnome have a writeable option?

A question though, how does this affect the "security" of the files in /Music, now that they are writeable/deletable ?  Assuming as long as only samba users can perform this function? This directory is also served up by Apache to the internet, accessible via a php script for downloading and streaming, and also viewable under smb:/

Oh yes, John just stays logged in so that Tom can get at his files. I need this because Bill is headless and I use xvnc to access Bill for changes.

---

### Post by Iowan on 2006-05-03
Unfortunately, my trusty Samba book is at home... but there is a **write access =**, or **write list =** (or something similar) that gives only a select few the ability to write/delete on a share.

---

