---
title: "&quot;failed to mount windows server&quot; message when trying to connect to a share folder"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by ltk5 on 2010-04-04
I'm trying to share a folder between two ubuntu PCs.

This is what I get when i try to connect to a folder i shared with nautilus (right click > share). I can get to Network > Windows Network > my desktop-pc, and I can see the folders (with both ubuntu pcs). I can also open the print$ folder (I get asked for the pw) but I can't do that with the other two: COLLECTION and shareltk. I use the gufw firewall.

I tried some of the how-tos with no luck, so I guess I'm doing something wrong, or I just don't know what to do...?

maybe it helps, this is what I get when running smbtree:
> 
Password: 
HOBOTNICA
	\\LOTKO-DESKTOP  		lotko-desktop server (Samba, Ubuntu)
		\\LOTKO-DESKTOP\shareltk       	
		\\LOTKO-DESKTOP\HP_LaserJet_1020	HP_LaserJet_1020
		\\LOTKO-DESKTOP\HP_LaserJet_10202	HP_LaserJet_10202
		\\LOTKO-DESKTOP\PDF            	PDF
		\\LOTKO-DESKTOP\Phaser_3117    	Xerox Phaser 3117
		\\LOTKO-DESKTOP\PIXMA-iP2000   	PIXMA-iP2000
		\\LOTKO-DESKTOP\IPC$           	IPC Service (lotko-desktop server (Samba, Ubuntu))
		\\LOTKO-DESKTOP\COLLECTION     	
		\\LOTKO-DESKTOP\print$         	Printer Drivers

---

### Post by ltk5 on 2010-04-04
bump

---

### Post by Iowan on 2010-04-04
Recommending [NFS]("http://ubuntuforums.org/showthread.php?t=249889") for sharing might be one option, but not if you plan to use the shares for Windows boxes, too. [Here]("http://ubuntuforums.org/showthread.php?t=1169149") is a How-To that *might* be helpful.

---

### Post by Morbius1 on 2010-04-04
(1) I'd disable the firewall and try again. If it works then at least you'd know the cause.

(2) Post the output of the following commands so we can see how your shares are set up:

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**
Type **testparm -s**

(3) Also need to know the permissions on the target directories that represent the shares: **COLLECTION and shareltk**.

The general form of the command is like this:

**ls -dl /path-to-shared-folder**

---

### Post by ltk5 on 2010-04-05
Firewall is disabled.

net usershare info
> [collection]
path=/home/lotko/torrent/COLLECTION
comment=
usershare_acl=Everyone:R
guest_ok=y

[shareltk]
path=/home/lotko/torrent/COLLECTION/shareltk
comment=
usershare_acl=Everyone:F
guest_ok=y

sudo net usershare doesn't give me anything

testparm -s:
> Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[cdrom]"
Processing section "[COLLECTION]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = HOBOTNICA
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

[cdrom]
	comment = Samba server's CD-ROM
	path = /cdrom
	guest ok = Yes
	locking = No

[COLLECTION]
	path = /home/lotko/torrent/COLLECTION
	guest ok = Yes
 I did edit smb.conf before, so there could be some errors.  Uncommenting the CD-rom section was just a test, it's not needed.

Permissions:
> drwxrwxrwx 405 lotko lotko 20480 2010-04-04 12:52 /home/lotko/torrent/COLLECTION/

drwxr-xr-x 2 lotko lotko 4096 2010-04-02 20:49 /home/lotko/torrent/COLLECTION/shareltk/

actually the only folder I'd like to share is Collection, shareltk was just a test.

---

### Post by Morbius1 on 2010-04-05
There is something very odd about all this.

**First**, there are two completely different methods of samba sharing - Nautilus-share and Classic-share and you're using both at the same time and on the same target directory. I would eliminate one form of sharing.

**Second**, you're using Nautilus-share on the shareltk folder:
> [shareltk]
path=/home/lotko/torrent/COLLECTION/shareltk
comment=
usershare_acl=[COLOR=Blue]Everyone:F[/COLOR]
guest_ok=y                      You're allowing guest access and write permissions but your linux file permissions:
>  [COLOR=Blue]drwxr-xr-x[/COLOR] 2 lotko lotko 4096 2010-04-02 20:49 /home/lotko/torrent/COLLECTION/shareltk/                      are allowing only read access to guests. And that's the odd part. One of the advantages of using Nautilus-share is that it will automatically modify linux permissions to allow guest access when you create the share. It should have changed the permissions to this:
>  [COLOR=Blue]drwxrwxrwx [/COLOR]2 lotko lotko 4096 2010-04-02 20:49 /home/lotko/torrent/COLLECTION/shareltk/                      But it didn't and I'm not exactly sure why it didn't.

This is one of those rare situations where I would recommend not using Nautilus-share. Something's just not right here. So I would go back to Nautilus and "unshare" both of these:
> [collection]
path=/home/lotko/torrent/COLLECTION
comment=
usershare_acl=Everyone:R
guest_ok=y

[shareltk]
path=/home/lotko/torrent/COLLECTION/shareltk
comment=
usershare_acl=Everyone:F
guest_ok=y                      That will leave you with only one Classic-share:
> [COLLECTION]
    path = /home/lotko/torrent/COLLECTION
    guest ok = Yes                      Which will allow guest access with read only permissions.

**Third**, and this is a long shot, make sure that the "torrent" directory has the executable bit enabled or else the remote user will not get to the COLLECTION folder. If you do an **ls -dl /home/lotko/torrent** there should be 3 "x" at a minimum - for example:

[B]ls -dl /home/lotko/torrent
[/B][COLOR=Blue]drwxr-xr-x
It has to have 3 "x"  's
[/COLOR]

---

### Post by ltk5 on 2010-04-05
The problem with the permissions could happen, because I was changing them. And so I probably changed them after sharing with nautilus-share thinking I'm doing an ok thing.

I unchecked nautilus-share on both folders. Then I edited permission on the 'torrent' folder to executable. After that I rebooted my system. I don't see the 'shareltk' folder anymore, 'COLLECTION' is still there and also the problem. 'cdrom' and 'print$' I can access without problems.

Here are the current permissions:
```

drwxr-xr-x 49 lotko lotko 12288 2010-03-27 22:07 /home/lotko/torrent

drwxr-xr-x 405 lotko lotko 20480 2010-04-04 12:52 /home/lotko/torrent/COLLECTION/

```
It looks as I can't change permissions for 'torrent' although it is executable.

---

### Post by Morbius1 on 2010-04-05
Actually ,

> drwxr-xr-x 49 lotko lotko 12288 2010-03-27 22:07 /home/lotko/torrent

drwxr-xr-x 405 lotko lotko 20480 2010-04-04 12:52 /home/lotko/torrent/COLLECTION/is completely correct and consistent with a samba share that is allowing read only access to guests. The problem is somewhere else.

Is it at all possible that the contents of /home/lotko/torrent/COLLECTION is readable only to lotko?

**ls -al /home/lotko/torrent/COLLECTION**

will tell you who owns the files in that directory and the permissions of the individual files.

---

### Post by ltk5 on 2010-04-06
Hm.. he's the only one mentioned.

> drwxr-xr-x   2 lotko lotko      4096 2009-10-17 13:53 
Most (all) files have this permission.

---

