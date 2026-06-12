---
title: "Share files on external Drive"
date: 2011-04-07
forum: Networking &amp; Wireless
---

### Post by RESQUIVEL on 2011-04-07
In ubuntu 10 when i want to share a folder just go to that folder

right clic>sharing options

Activate:
 share this folder
 Allow others to create and delete files in this folder
 Guest access (for people without a user acount)

click on Modify share button

in other computer I go to Places>Network doble clic in the computer with share folder, double click in the share folder, and I can access to the files

If the share folder is in the internal hard drive all runs good, but if I share a folder in a external drive, when i go to places>network doble clic in the computer icon, i see the share folder BUT when I made doble clic on to open it

'Unable to mount location Failed to mount windows share'

what happen!!!

---

### Post by Dojan on 2011-04-14
I am having the same problem but with an internal hdd on my Lubuntu server. I can access the disk fine from the server as you'd expect, and I can access anything shared from the root disk from any other computer on the network, but whenever I try to access the extra disk over the network I get the "Unable to mount location, Failed to mount Windows share" message. 
Which is kind of a downer, since i setup the server and bought that disk for exactly that purpose :)

The disk is a Western Digital Caviar Green with Advanced Formating Technology, could it have anything to do with that?

---

### Post by Morbius1 on 2011-04-14
> If the share folder is in the internal hard drive all runs good, but if I  share a folder in a external drive, when i go to places>network  doble clic in the computer icon, i see the share folder BUT when I made  doble clic on to open it

'Unable to mount location Failed to mount windows share'

what happen!!!Is the external drive formatted in ntfs or fat32? if it is and in mounts when plugged in then it will mount with you as owner and with permisssions to allow only you to access it. The remote guest is not you so access is denied. THe easiest way out of this is to add the following command to your smb.conf file:
```
force user = morbius
```[COLOR=Blue]*Change morbius to your own local login user name.*[/COLOR]

Then restart samba: sudo service smbd restart.

Where you put that line depends on what method you used to create the share - there are 2.

If you used Nautilus to create the share then add the line to the [global] section of smb.conf. If you used the Classical method then add it to the share definition itself in smb.conf.

---

### Post by Dojan on 2011-04-14
Thanks for the reply!

Unfortunately it doesn't seem to work... 
This should be done at the serving end right?
Yes my drive is an NTFS for Win7 compatibility...

When trying to access it from another computer (one of my old rigs, now folding@home headlessly full-time, also running Lubuntu :)) I don't even see that folder shared?? It is still listed amongst the shared folder, and I still see it from my main computer, but still can't access it though...

Confused!

---

### Post by Morbius1 on 2011-04-14
I wasn't responding to you I was responding to the original poster. He has an external partition and you have an internal partition.

I don't understand your problem:
> I don't even see that folder shared?? It is still listed amongst the  shared folder, and I still see it from my main computer, but still can't  access it though...You can't see the folder -- but it's listed -- And you can see it from the other computer. I don't know what that all means.

If you post the output of the following commands it might make more sense:
```
testparm -s
smbtree
```

---

### Post by HaydarFuel on 2011-04-14
thanks morbius1, you helped me share files on ntfs it worked :D

---

### Post by Tigaernach on 2011-04-15
Oh man this has been bothering me for so long. Thanks a bunch, I didn't think the solution would be that simple!

---

### Post by Dojan on 2011-04-16
@ Morbius1
Ok, sorry for the thread-jacking. :oops:

Here is a hopefully better explanation:
I've got a home-network with; 
1 server running Lubuntu 10.10, 
3 desktops; 
  the one I am using right now running Ubuntu 10.10, 
  one for my girlfriend running windows 7, 
  and my old rig, standing in a closet folding@home, running Lubuntu 10.10.
1 laptop with Ubuntu 10.10.

The other day I got a new 2TB HDD, a Western Digital Green AF, and put it in the server, with all our stuff on it, formated to NTFS to share over the network. Using the Main Menu-->Preferences-->Shared Folders (in Lubuntu that is, in Ubuntu it is of course System-->Administration-->Shared Folders) utility, i am able to easily and without problems share any folder in the root disk, and on access that share on any other computer; However when I try to share the new disk, it seems to work as long as I sit by the server; I can access files etc, and the Share Folders app doesn't complain. But when I try to access that disk from my Ubuntu computers I get the "Unable to mount location, Failed to mount Windows share" message; When trying on the Win7 machine I get a windows error code, and (this is the confusing bit) when I try to access it from my old rig running Lubuntu, the shares from the server root disk shows up fine, but the new disk doesn't even show up at all, like it wasn't there.

---

### Post by Morbius1 on 2011-04-17
@Dojan

As a side point, there was no need to format the 2nd drive in NTFS "for Win7 compatibility" if the Win7 machine was on the network. Samba ( CIFS ) uses a virtual file system all it's own.

"Unable to mount location, Failed to mount Windows share" is most likely not a Samba issue but a Linux file permissions problem and I'm guessing due to how you are mounting the ntfs drive.

Since you didn't provide the information I ask for in my earlier post you're not likely to provide this either but if you post the output of these commands I might just be able to help you:
```
cat /etc/fstab
sudo blkid -c /dev/null
mount
```

---

### Post by Dojan on 2011-04-17
Okay, your first point is interesting, thanks for the heads up!

Ok, here is the first piece of information you requested, sorry for missing that...

```
dojan@Server:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[dojan]"
Processing section "[HemmaDisk]"
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
	force user = dojan

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[dojan]
	path = /home/dojan
	read only = No
	guest ok = Yes

[HemmaDisk]
	path = /media/59E10C3A72269DB7
	guest ok = Yes
dojan@Server:~$ smbtree
Enter dojan's password: 
WORKGROUP
	\\SERVER         		Server server (Samba, Ubuntu)
		\\SERVER\IPC$           	IPC Service (Server server (Samba, Ubuntu))
		\\SERVER\HemmaDisk      	
		\\SERVER\dojan          	
		\\SERVER\print$         	Printer Drivers
	\\DOJANFAH-AMD-MIK		DojanFaH-AMD-Mikaelas-gamla server (Samba, Ubunt
		\\DOJANFAH-AMD-MIK\print$         	Printer Drivers
		\\DOJANFAH-AMD-MIK\dojan          	
		\\DOJANFAH-AMD-MIK\IPC$           	IPC Service (DojanFaH-AMD-Mikaelas-gamla server (Samba, Ubuntu))
	\\DOJAN-AMD-DESKT		dojan-AMD-DeskTop server (Samba, Ubuntu)
		\\DOJAN-AMD-DESKT\IPC$           	IPC Service (dojan-AMD-DeskTop server (Samba, Ubuntu))
		\\DOJAN-AMD-DESKT\dojan-AMD-DeskTop	
		\\DOJAN-AMD-DESKT\print$         	Printer Drivers
dojan@Server:~$ 
```

And the second piece:

```
dojan@Server:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=b4555308-2acc-4944-9240-23088eb5d810 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=56125154-85bc-4e85-bcdc-a05b4c907b1a none            swap    sw              0       0
dojan@Server:~$ sudo blkid -c /dev/null
[sudo] password for dojan: 
/dev/sdb1: UUID="" TYPE="ntfs" 
/dev/sda1: UUID="56125154-85bc-4e85-bcdc-a05b4c907b1a" TYPE="swap" 
/dev/sda2: LABEL="LINUX" UUID="b4555308-2acc-4944-9240-23088eb5d810" TYPE="ext4" 
dojan@Server:~$ 
```

To clarify: The 2TB disk's name is 59E10C3A72269DB7. Dunno how that happened...

Thanks!

---

### Post by Morbius1 on 2011-04-17
You have no entry in /etc/fstab for the ntfs partition so you are mounting it through Places I guess. That will mount with you as owner and with access limited to you alone. Your smb.conf with the force user included should work but you have to  remember to mount the ntfs partition first or else no one will be able  to access it.

You could automount this partition at boot with the correct permissions but there's a problem I've never seen before. The output of blkid:
> sudo blkid -c /dev/null
/dev/sdb1: UUID="" TYPE="ntfs"Every partition has a UUID. I don't know how it could not have a UUID. If a partition doesn't have a lablel Places will mount it to /media/UUID and in this case it mounts it to /media/59E10C3A72269DB7. So Places thinks it has a UUID and blkid does not? I'm at a loss on that one.

You can create an entry in /etc/fstab that does not reference the UUID , for example:
```
/dev/sdb1 /media/Data ntfs defaults,uid=1000,umask=000,nls=utf8 0 0
```*Note: You would have to create the /media/Data mount point first.*

And then mount it with a sudo mount -a

But I would be hesitant to recommend doing that since I'm not sure what it means when a partition has no UUID. Something isn't right here.

---

### Post by Chessmaster on 2012-01-09
thanks Morbius1. 

You have saved me from what was become quite a headache. Now my WDTV happily reads my external HHD samba share. 

Cheers

---

