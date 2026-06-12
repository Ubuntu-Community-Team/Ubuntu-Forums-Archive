---
title: "Need help with Samba"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by sixstorm on 2010-06-09
I've just started using Ubuntu as my primary OS this week (long story) but I use my main workstation for more than just web surfing.  I use it to game and to share things like movies, music, pictures, software, etc.

Currently I have:

(1) 320GB Windows 7 Hard Drive
(1) 160GB Ubuntu 10.04 Hard Drive
(1) 1TB Storage Hard Drive

I have a few folders on the Storage drive that I share to my HTPC, which has mapped network drives already setup for Boxee.  I'm basically wanting to have the folders shared, whether I can set it up once and go about my life, or if I need to run a script each time I reboot.  

I've noticed that when I try to share the folders off of the Storage drive, I get access denied all day long, mainly because it's on another hard drive.  Anything I share on the Ubuntu Hard Drive, it will share all day long.  

Any clues guys?

---

### Post by sixstorm on 2010-06-11
Just wanted to give this thread a bump and see if anyone could give me any direction.  Thanks.

---

### Post by Morbius1 on 2010-06-11
If it's an "access denied" message it's likely a linux permissions error not a samba error. But to make sure please post the output of the following commands so we can see how you're set up:

```
net usershare info
sudo net usershare info
testparm -s
```

---

### Post by sixstorm on 2010-06-11
> **Morbius1 said:**
> If it's an "access denied" message it's likely a linux permissions error not a samba error. But to make sure please post the output of the following commands so we can see how you're set up:

```
net usershare info
sudo net usershare info
testparm -s
```

I'll do that later tonight when I get home.

---

### Post by sixstorm on 2010-06-11
Here you go.  These are the permissions that I wanna use in the end, but I just want to get it working first.  Thanks.

```
net usershare info
[storage]
path=/media/Storage
comment=
usershare_acl=Everyone:R,
guest_ok=n

[movies]
path=/media/Storage/Movies
comment=
usershare_acl=Everyone:R,
guest_ok=n

```

```
testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Movies]"
Processing section "[Downloads]"
Processing section "[Storage]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = BLACKBOX
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
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Movies]
	comment = Movies
	path = /media/Storage/Movies
	read only = No
	guest ok = Yes

[Downloads]
	path = /home/andrew/Downloads
	read only = No
	guest ok = Yes

[Storage]
	path = /media/Storage
	read only = No
	guest ok = Yes

```

---

### Post by Morbius1 on 2010-06-11
There's a couple of problems here. 

First, and I'll admit it's not documented at all, but there are two completely different methods of using Samba to share files: 

Nautilus-share ( tight click a folder in Nautilus > Sharing Options ) and Classic -shares. Your using both at the same time ( not recommended ) and worse you're using both on the same target folder. For example:
** Nautilus-share:**
> [storage]
path=/media/Storage
comment=
usershare_acl=Everyone:R,
guest_ok=n
**Classic-share:**
> [Storage]
    path = /media/Storage
    read only = No
    guest ok = YesYou notice that the two shares even have different settings - one allows guest access and the other does not. Samba is confused.

DO you have a preference for what method you want to use. The one advantage Nautilus-shares is that it modifies permissions automatically but that can be done with Classic-shares with a little more effort.

Also just to anticipate a future problem, is /media/Storage an external NTFS or FAT32 drive by any chance. And what are it's permissions:
```
ls -dl /media/Storage
```

---

### Post by sixstorm on 2010-06-11
> **Morbius1 said:**
> There's a couple of problems here. 

First, and I'll admit it's not documented at all, but there are two completely different methods of using Samba to share files: 

Nautilus-share ( tight click a folder in Nautilus > Sharing Options ) and Classic -shares. Your using both at the same time ( not recommended ) and worse you're using both on the same target folder. For example:
** Nautilus-share:**
**Classic-share:**
You notice that the two shares even have different settings - one allows guest access and the other does not. Samba is confused.

DO you have a preference for what method you want to use. The one advantage Nautilus-shares is that it modifies permissions automatically but that can be done with Classic-shares with a little more effort.

Also just to anticipate a future problem, is /media/Storage an external NTFS or FAT32 drive by any chance. And what are it's permissions:
```
ls -dl /media/Storage
```

Makes sense.  I'd like to just use the Nautilus path but if I need to always configure Samba's conf file, I can do that too.  The "Storage" hard drive is NTFS.

Here is more output:

```
drwx------ 1 andrew andrew 16384 2010-06-06 10:05 /media/Storage

```

---

### Post by Morbius1 on 2010-06-11
I guess the fastest way to do this is to remove the classic-shares first. If you used the Samba-GUI just go back in and remove the shares. That will leave you with only the Nautilus-shares.

Next, go back into Nautilus and go to:

/media/Storage
/media/Storage/Movies
/home/andrew/Downloads

Right click on each one > Sharing Options > Make sure all three boxes are checked > Create Share

Now we need to make one addition to smb.conf to overcome the permissions problem on the NTFS drive. Right now only "andrew" can access that drive regardless of what samba says so you need to add a line to fix it:

Open gedit as root in a Terminal:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [COLOR=Blue][global] [/COLOR]section of smb.conf:
```
force user = andrew
```Save the file, exit gedit, and back in the terminal restart samba:

If you're using Ubuntu 10.04:
```
sudo service smbd restart
sudo service nmbd restart
```If you're using an earlier version:
```
sudo service samba restart
```

---

### Post by Morbius1 on 2010-06-11
I hate to leave you at this time but I've got to pack it in for the day. Hopefully the above instructions should have produced 3 public shares accessable by anyone on the network.

If you want more control over that then you need to uncheck the "guest access" box in nautilus for that share. This will require the remote user to supply a username and password to gain access. This requires two steps on your box:

(1) Each remote user actually has to have an account on your box. You can create an account with no local login this way:

Let's say the remote user is named mary:
In a Terminal:
```
sudo useradd -s /bin/true mary
```[COLOR=Blue]*This will create a mary user on the server that has no server logon capability and no server home directory.*[/COLOR]

(2) Now create a samba password for mary to use to access your share:
```
sudo smbpasswd -a mary
```*[COLOR=Blue]This will add and enable a samba user named mary with the password that mary will use to access your share[/COLOR]*

---

### Post by sixstorm on 2010-06-11
Thanks for the help!  

I was finally able to map the network drives on my Windows 7 HTPC with no issues.  Thanks again for your help.

I'll have to work out permissions later as really, there isn't any need for them at this point.

---

