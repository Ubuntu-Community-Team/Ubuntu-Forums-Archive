---
title: "mount network share help, please"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by stanleytberry on 2010-03-24
I am a windows user.  I have determined that I must convert to Linux.  I have several applications that I must find equivalents for (personal finance, e-mail, calendar, …) and for all of them I have found programs that I think will provide the function my wife and I require.  I have an 1141 page “A Practical Guide to UBUNTU Linux” and O'Reilly's 927 page “LINUX In a Nutshell” and I've scoured them both.  I've searched the UBUNTU Community documentation and forums.  My problems are the simple things … like mounting a network share.   I currently have all our critical data on a NetGear NasServer.  What I cannot seem to discover how to do is to mount a share from that server on my UBUNTU 9.10 desktop system.  Can someone tell me what did I miss, please?

I installed Ubuntu desktop 9.10.

I made ONLY these changes to the installed system (rebooting every time I saved a change):
[LIST=1]
[*]created xorg.conf and set the monitor to match my physical monitor
[*]did “aptitude install smbfs” ('the only package needed to mount a Windows share' per page 825 in my Practical Guide) and verified that mount.cifs now exists in /sbin (it didn't before)
[*]created group “samba” and added myself to that group (setting up Samba in the community documentation)
[*]did “sudo visudo” and added %samba ALL=(ALL) /bin/mount,/bin/umount,/sbin/mount.cifs,/sbin/umount.cifs (setting up Samba in the community documentation) and verified that /etc/sudoers now contains that line
[*]did “mkdir money” in my home directory (see below)
[*]did “smbtree” and verified that the share in which I'm interested is visible (see below)
[/LIST] 

```
stan@stanDesktop:~$ ls -l

total 40

drwxr-xr-x 2 stan stan 4096 2010-03-24 08:17 Desktop

drwxr-xr-x 2 stan stan 4096 2010-03-24 08:17 Documents

drwxr-xr-x 2 stan stan 4096 2010-03-24 08:17 Downloads

-rw-r--r-- 1 stan stan  167 2010-03-24 08:01 examples.desktop

drwxr-xr-x 2 stan stan 4096 2010-03-24 08:40 money

drwxr-xr-x 2 stan stan 4096 2010-03-24 08:17 Music

drwxr-xr-x 2 stan stan 4096 2010-03-24 08:17 Pictures

drwxr-xr-x 2 stan stan 4096 2010-03-24 08:17 Public

drwxr-xr-x 2 stan stan 4096 2010-03-24 08:17 Templates

drwxr-xr-x 2 stan stan 4096 2010-03-24 08:17 Videos

stan@stanDesktop:~$ 
```

```
stan@stanDesktop:~$ smbtree

Enter stan's password: 

WORKGROUP

	\\SANDYMAGED-PC  		

	\\000000E226DF   		MP620 series

		\\000000E226DF\canon_memory   	MP620 series

		\\000000E226DF\IPC$           	

	\\000000C3855B   		MX700 series

		\\000000C3855B\canon_memory   	MX700 series

		\\000000C3855B\IPC$           	

HOMEGROUP

	\\TRAYLORPC      		

		\\TRAYLORPC\PicturesMaster-Backup	

		\\TRAYLORPC\C$             	Default share

		\\TRAYLORPC\ADMIN$         	Remote Admin

		\\TRAYLORPC\System-Backup  	

		\\TRAYLORPC\F$             	Default share

		\\TRAYLORPC\KX-P2023       	Panasonic KX-P2023

		\\TRAYLORPC\Envelopes-Backup	

		\\TRAYLORPC\DatabaseMaster-Backup	

		\\TRAYLORPC\Money-Backup   	

		\\TRAYLORPC\Letters-Backup 	

		\\TRAYLORPC\Calendar-Backup	

		\\TRAYLORPC\Archives-Backup	

		\\TRAYLORPC\print$         	Printer Drivers

		\\TRAYLORPC\IPC$           	Remote IPC

		\\TRAYLORPC\Workstation-Backup	

		\\TRAYLORPC\Cardfile-Backup	

		\\TRAYLORPC\E$             	Default share

	\\ROAMINGPC      		

		\\ROAMINGPC\C$             	Default share

		\\ROAMINGPC\ADMIN$         	Remote Admin

		\\ROAMINGPC\D$             	Default share

		\\ROAMINGPC\IPC$           	Remote IPC

		\\ROAMINGPC\OpenVPNconfig  	

	\\NASSERVER      		nasServer

		\\NASSERVER\Archives       	Stan-and-Jeanne.us archives

		\\NASSERVER\Calendar       	Stan-and-Jeanne.us calendar data

		\\NASSERVER\Cardfile       	Stan-and-Jeanne.us contact data

		\\NASSERVER\DatabaseMaster 	Stan-and-Jeanne.us master database

		\\NASSERVER\Envelopes      	Stan-and-Jeanne.us envelopes

		\\NASSERVER\Genealogy      	

		\\NASSERVER\Letters        	Stan-and-Jeanne.us letters

		\\NASSERVER\LogFiles       	

		\\NASSERVER\Money          	Stan-and-Jeanne.us financial data

		\\NASSERVER\PicturesMaster 	Stan-and-Jeanne.us master pictures

		\\NASSERVER\System         	Stan-and-Jeanne.us system data

		\\NASSERVER\WWWContent     	Stan-and-Jeanne.us web content

		\\NASSERVER\backup         	Backup Share

		\\NASSERVER\icons          	collected icon images

		\\NASSERVER\media          	Media Server Share

		\\NASSERVER\stuff          	stuff Stan's installed

		\\NASSERVER\x-mas          	anything associated with the holiday season

		\\NASSERVER\IPC$           	IPC Service (nasServer)

	\\JEANNEPC       		

		\\JEANNEPC\C$             	Default share

		\\JEANNEPC\ADMIN$         	Remote Admin

		\\JEANNEPC\IPC$           	Remote IPC

stan@stanDesktop:~$ 
```
```

stan@stanDesktop:~$ mount -t cifs //NASSERVER/Money money
 (\\NASSERVER\Money same result)
mount: only root can do that

stan@stanDesktop:~$ sudo mount -t cifs //NASSERVER/Money money

[sudo] password for stan: 

Password: 

mount error(13): Permission denied

Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

stan@stanDesktop:~$
``` 


What did I miss, please?

---

### Post by Iowan on 2010-03-24
Here's a couple of How-To's for mounting Samba (CIFS) shares:
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")
[http://ubuntuforums.org/showthread.php?t=1186877]("http://ubuntuforums.org/showthread.php?t=1186877")

---

### Post by johnson.d on 2010-03-25
You can use the command as follows:

```
$ sudo mount -t cifs //NASSERVER/Money money -o user=<user-id>
```

where the user-id is the username to which the permission has been given.

---

### Post by stanleytberry on 2010-03-25
Permission on what?  The share? ... no user/password defined; the mount point? ... I specify -0 user=stan and enter stan's login password when it asks for it and it fails in the same way ... permission denied, SAMBA? I tried changing passdb backend in smb.conf to 'smbpasswd' ... no difference.

And why won't it let stan issue the mount?  If I don't use 'sudo' it says only root can use mount.

I built an 8.04 LAMP server which mounts a share (read only) from the same NAS server and serves up pictures from the mounted share ([http://www.Stan-and-Jeanne.com](http://www.Stan-and-Jeanne.com)).  When I set it up 6 months ago or so I think all I had to do was put it in fstab and it worked.

This is so frustrating!

---

### Post by johnson.d on 2010-03-25
The following thread has a detailed method of mounting the Windows share.

[http://ubuntuforums.org/showthread.php?t=1409720](http://ubuntuforums.org/showthread.php?t=1409720)

---

### Post by stanleytberry on 2010-03-27
Save specific names, I did exactly what that post said.  My result is still the same:
```
stan@stanDesktop:~$ sudo mount -a
[sudo] password for stan: 
Password: 
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
stan@stanDesktop:~$ 
```
I entered my password at the prompt for [sudo] and then I get the second prompt 'Password:'.  It doesn't matter what I enter, hit 'Enter', type in a password, it fails in the same manner.  It doesn't matter where is the mount point or whether I create it as 'stan' our using 'sudo'.

I've looked at 'man mount.cifs' and I really can't make a connection.  The share I'm trying to mount has no permissions and I can 'mount' it on my desktop with the File Browser and see the contents.

But I want it at some mount point to which I can point an application ... like KMyMoney.

Where does that second prompt for 'Password:' come from?  How can I find out?

Thanks,

---

### Post by stanleytberry on 2010-03-28
Here's what I did:
[LIST]
[*]installed UBUNTU Desktop 9.10 on a clean machine
[*]allowed the Update Manager to apply all updates
[*]created xorg.conf in /etc/X11 and modified it to use my monitor
[*]opened a terminal and entered 'xset mouse 22/8 0' to make my mouse work similar to the way it does on my Windows 2000 workstation
[*]used the Update Manager to install package smbfs
[*]used the File Browser to ensure that I could open and modify a file on the share I wish to mount
[INDENT]it left a link (? … funny little curly arrow at the bottom of a folder icon pointing to a black dot in the middle of a small white box in the middle of the icon) on my UBUNTU desktop which opens the share if I double-click on it[/INDENT]
[*]went back to Windows 2000, opened the share and verified that the modification was there
[*]followed the instructions in suseendran.rengabashyam's  forum append ([http://ubuntuforums.org/showthread.php?t=1409720](http://ubuntuforums.org/showthread.php?t=1409720))[/LIST]

Here's the fstab entry:
[INDENT]//nasServer/Money /shares/money cifs uid=1000,gid=1000 0 0[/INDENT]

Here's the folder I created to hold mount points (ls -l):
[INDENT]drwxrwxrwx   3 root root  4096 2010-03-26 16:56 shares[/INDENT]
and its contents (ls):
[INDENT]money[/INDENT]

Here's the folder to be used as the mount point for this exercise (ls -l):
[INDENT]drwxrwxrwx 2 root root 4096 2010-03-26 16:56 money[/INDENT]

Here's the command (I just hit enter at the Password: prompt):
[INDENT]stan@stanDesktop:/$ sudo mount --verbose -a

mount: proc already mounted on /proc

Password: 



mount.cifs kernel mount options: unc=//nasServer\Money,user=root,ver=1,rw,uid=1000,gid=1000,ip=192.168.48.5,pass=********

mount error(13): Permission denied

Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

stan@stanDesktop:/$[/INDENT]
I don't understand “mount: proc already mounted on /proc” and I don't understand where the Password: prompt comes from and I don't understand why there is a pass=******** on the mount options string.  The ip address is correct.

There are no permissions on the share.

Is there anyone who can tell me what's going on, please?

Thanks,

---

### Post by Morbius1 on 2010-03-28
**First**, maybe it's too early in the morning for me but it looks like you are not specifying who you are to the server in the fstab entry:
> //nasServer/Money /shares/money cifs uid=1000,gid=1000 0 0If the server allows guest access it should be something like this:
```
//nasServer/Money /shares/money cifs guest,uid=1000,gid=1000 0 0
```If the server requires authentication it should look something like this:
```
//nasServer/Money /shares/money cifs username=server_user,password=secret,uid=1000,gid=1000 0 0
```**Second**, just so I understand this comment:
> used the File Browser to ensure that I could open and modify a file on the share I wish to mountYou're using Nautilus to browse to the share and mounting it that way?

You may not realize this but nautilus actually creates a mount point automatically. It's located at:

**/home/stan/.gvfs/....**

---

### Post by stanleytberry on 2010-03-28
Added 'guest' ...
[INDENT]stan@stanDesktop:~$ sudo mount --verbose -a
mount: proc already mounted on /proc

mount.cifs kernel mount options: unc=//nasServer\Money,user=,ver=1,rw,guest,uid=1000,gid=1000,ip=192.168.48.5
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)[/INDENT]
... no Passwd: prompt but it still fails in the same way?

If Nautilus = the File Browser then yes.  I found it by clicking Places and then clicking Computer.  I then clicked on a groupname and then clicked on the servername and then clicked on the sharename and ... voila! ... I could see and edit data on that share.

I found .gvfs in /home/stan but I can't seem to access it.  Is the share really mounted there?  How would I tell KMyMoney to store its data file there?

---

### Post by stanleytberry on 2010-03-28
AHA! Got it!
[INDENT]stan@stanDesktop:~$ cd ../..
stan@stanDesktop:/$ cd /home/stan/.gvfs
[email]stan@stanDesktop:~/.gvfs[/email]$ ls
money on nasserver
[email]stan@stanDesktop:~/.gvfs[/email]$ ls
money on nasserver
[email]stan@stanDesktop:~/.gvfs[/email]$ cd money on nasserver
bash: cd: money: No such file or directory
[email]stan@stanDesktop:~/.gvfs[/email]$ cd "money on nasserver"
[email]stan@stanDesktop:~/.gvfs[/email]/money on nasserver$ ls
2007-09-21 saved before reinstituting server based Money  CPI                            life insurance             spread sheets
2010-03-21 Export MySmartCash Account Data.qif            created document               Maged support documents    stock prices
2010-03-22 Export 11907 Helene Court Data.qif             financial plan (historical)    newQDATA.mny               taxes
2010-03-22 Export HFCU Draft Account Data.qif             HFCU Bill Payer Guarantee.pdf  Quicken_Data (historical)  utilities history.pdf
2010-03-22 Export HFCU Share Account Data.qif             IRS Forms                      saved 2006-09-28 Money
2010-03-22 Export HFCU VISA Account Data.qif              KMyMoney                       Social Security
[email]stan@stanDesktop:~/.gvfs[/email]/money on nasserver$ [/INDENT]
I'd still rather have it where I want it.  I still don't understand why I can't get it to mount.

---

### Post by Morbius1 on 2010-03-28
> I'd still rather have it where I want it.  I still don't understand why I can't get it to mount.     I don't quite understand why it doesn't work using the fstab method either. It's probably something obvious that we're both missing.

As for the gvfs mount point, you could create a symlink from the "hidden" directory to a "real" directory. For example:

[B]ln -s /home/stan/.gvfs /shares

OR 

[/B]**ln -s /home/stan/.gvfs/****"money on nasserver"**** /shares****/money**

Or some variation of these ;)

---

### Post by stanleytberry on 2010-03-28
OK.  Thanks.  Someday I'll figure it all out.  This'll get me started.

---

### Post by stanleytberry on 2010-03-30
Well ...

This worked:
[INDENT]stan@stanDesktop:~/.gvfs/money on nasserver$ ln -s * ~/money
stan@stanDesktop:~$ cd money
stan@stanDesktop:~/money$ ls
[INDENT]2007-09-21 saved before reinstituting server based Money  CPI                            life insurance             spread sheets
2010-03-21 Export MySmartCash Account Data.qif            created document               Maged support documents    stock prices
2010-03-22 Export 11907 Helene Court Data.qif             financial plan (historical)    newQDATA.mny               taxes
2010-03-22 Export HFCU Draft Account Data.qif             HFCU Bill Payer Guarantee.pdf  Quicken_Data (historical)  utilities history.pdf
2010-03-22 Export HFCU Share Account Data.qif             IRS Forms                      saved 2006-09-28 Money
2010-03-22 Export HFCU VISA Account Data.qif              KMyMoney                       Social Security[/INDENT][/INDENT]
BUT … if I try and open a folder in money I get
[INDENT]stan@stanDesktop:~/money$ cd KMyMoney
bash: cd: KMyMoney: Too many levels of symbolic links
stan@stanDesktop:~/money$ cd taxes
bash: cd: taxes: Too many levels of symbolic links[/INDENT]
or in the File Browser I get a dialog stating the link is broken and do I want to move it to trash?

So … 
[LIST=1]
[*]How do I get rid of the symbolic links?
[*]Any thing else I could try?[/LIST]
Thanks,

---

### Post by stanleytberry on 2010-04-15
OK.  I just deleted the links and happily nothing else got deleted.

Even stranger, I discovered "panel"s and added one to my desktop.  I added a "drawer" to my panel.  In the drawer I added a "custom application launcher" (type = location, URL = smb://nasServer/Money/taxes/2009 Taxes) and when I click on it opens the folder without a whimper.  It also mounts the share on my Desktop ... and doesn't unmount it when I close the folder.

Why can't I just mount the share to some mount point using fstab?????

---

