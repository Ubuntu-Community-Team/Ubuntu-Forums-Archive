---
title: "Help with Samba"
date: 2012-08-17
forum: Networking &amp; Wireless
---

### Post by strange_cathect on 2012-08-17
Weird problem. When I use nautilus and try to "Browse Network" by opening shares on another computer in my network, I get an error message that Ubuntu "failed to retrieve share list from server."

However, if I open a terminal and type: nautilus smb://192.168.1.105, I can browse all the shares perfectly.

Can somone help me troubleshoot this?

Thanks!

---

### Post by Morbius1 on 2012-08-17
See if this helps. You never stated if the server is another Linux machine or a Windows machine so some of the items don't apply. The client machine though should do all of them.

[http://ubuntuforums.org/showpost.php?p=12164416&postcount=3](http://ubuntuforums.org/showpost.php?p=12164416&postcount=3)

Note: any time you restart samba the network has a hissy fit so you need to wait a few minutes for things to settle down before you try to "browse" the network again.

---

### Post by strange_cathect on 2012-08-17
Thanks for this.

The server and all clients run Ubuntu 12.04. I'll try this fix when I get home and see if that resolves things.

---

### Post by strange_cathect on 2012-08-18
Sadly, none of that worked. Is this a problem with nautilus?

---

### Post by Morbius1 on 2012-08-18
While we play with more diagnostics and since all machines are running ubuntu access the other machine this way:
```
nautilus smb://hostname.local
```
[COLOR=Blue]*Where hostname is the name of the other machine.*[/COLOR]

Back to the diagnostics, please post the output of the following command:
```
smbtree
```

---

### Post by strange_cathect on 2012-08-19
Using  "nautilus smb://basement.local" does work fine. Browsing there, however, still doesn't work.

Here is my info:

> WORKGROUP
	\\BASEMENT       		Basement server (Samba, Ubuntu)
		\\BASEMENT\Alan Backup    	
		\\BASEMENT\Music          	
		\\BASEMENT\IPC$           	IPC Service (Basement server (Samba, Ubuntu))
		\\BASEMENT\plexmedia      	
		\\BASEMENT\print$         	Printer Drivers
	\\ALAN-LAPTOP    		alan-laptop server (Samba, Ubuntu)
		\\ALAN-LAPTOP\Samsung-ML-1740	Samsung ML-1740
		\\ALAN-LAPTOP\IPC$           	IPC Service (alan-laptop server (Samba, Ubuntu))
		\\ALAN-LAPTOP\print$         	Printer Drivers
	\\ALAN-DESKTOP   		alan-desktop server (Samba, Ubuntu)
		\\ALAN-DESKTOP\The Hopper     	
		\\ALAN-DESKTOP\ML-1740        	Samsung ML-1740
		\\ALAN-DESKTOP\HP-Officejet-Pro-L7500	HP Officejet Pro L7500
		\\ALAN-DESKTOP\IPC$           	IPC Service (alan-desktop server
(Samba, Ubuntu))
		\\ALAN-DESKTOP\print$         	Printer Drivers

---

### Post by Morbius1 on 2012-08-19
Although I admit this is a side note to the original issue, you really have no need to browse to the basement machine. You can either run:
```
nautilus smb://192.168.1.105
```Or, if that machine doesn&#8217;t have a consistent static ip address:
```
nautilus smb://basement.local
```And when Nautilus opens up bookmark it: **Bookmarks > Add Bookmark**.

Anyway, the "failed to retrieve share list" is usually a name resolution problem but the output of smbtree should have resulted in an error if that were true. Instead it outputs everything just the way it should have.

You could try one more thing to narrow down where this problem is coming from. Access a specific share by name using this command from the terminal:
```
gvfs-mount smb://basement/Music
```** If it comes back to the prompt then it mounted the remote share successfully to $HOME/.gvfs and there does appear to be something odd about Nautilus in your case since it is clearly able to figure out the identity of "basement".

** If it comes back with an error suggesting it has no ideas who "basement" is then I don't have an answer consistant with the output of smbtree.

---

### Post by zamar28 on 2012-08-19
I've somewhat similar question and also need help. I can create Samba shares on Linux machine and browse them on Win7 PC. But when I dismount a shared device on Linux machine, its still remain visible as a shared drive in Win Explorer - Network (I don't assign a drive letter to it), and I can browse its empty folder.

If I stop Samba, the shared drives disappear - at times after reloading Explorer, or if not, the folders are no longer browsable.

So my question is, how to configure Samba server via terminal to automatically hide shared folders on a client PC (Windows or Linux), when the device was unmounted from the folder on server? Does it require running some extra script or just editing Samba config file?

As a separate question, how to delete obsolete Samba shares from Win Explorer after shutting down Linux machine, if they persist? Any command I can run on Linux machine to do that?

---

### Post by strange_cathect on 2012-08-19
No dice. I issued the command and the terminal worked for about 30-40 seconds, then replied:

~$ gvfs-mount smb://basement/Music

Error mounting location: Failed to mount Windows share

---

### Post by Morbius1 on 2012-08-19
>  Error mounting location: Failed to mount Windows shareThat's a different error message. That's not a name resolution problem that's a Linux permissions problem. When you get a moment run the following command from the "basement" machine and post it's output:
```
testparm -s
```And just in case this one ( if you didn't create any samba shares from Nautilus there will be no output ) :
```
net usershare info --long
```Side note: @zamar28, your post is about as far removed from this discussion as one can get and still be Samba related. I would respectfully suggest you start your own topic.

---

### Post by bootedguy on 2012-08-19
I have never had much luck with SMB shares and network browsing. But if all the machines are Linux, why not use NFS? It is the traditional protocol for networking in Linux, and is very solid.

---

### Post by Morbius1 on 2012-08-20
> **bootedguy said:**
> I have never had much luck with SMB shares and network browsing. But if all the machines are Linux, why not use NFS? It is the traditional protocol for networking in Linux, and is very solid.
Well, here's the thing. The OP doesn't have a problem with Samba since he can access the box by both ip address and by an mdns qualified host name:
> nautilus smb://192.168.1.105
nautilus smb://basement.local
I have tried to back away gracefully from this thread by pointing out that he can bookmark those locations so that he doesn't have to "browse" but it appears that he truly wants to know why he can't browse to that box.

---

### Post by strange_cathect on 2012-08-20
I really am just curious. And I appreciate your help. Plus, if I'm having this problem then others are too. If we identify some kind of  bug, then the rest of the community benefits. 

I'll be out of pocket today; I'll work on the basement machine later tonight.

**BTW: I'm using the windows share because some of the shared folders are used by multiple Roku devices. I've had problems with getting that to work**

---

### Post by strange_cathect on 2012-08-22
Here are those commands:


alan@Basement:~$ sudo testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[plexmedia]"
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
	name resolve order = bcast host lmhost wins
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[plexmedia]
	path = /var/lib/plexmedia
	read only = No
	guest ok = Yes


--------------------


alan@Basement:~$ sudo net usershare info --long

[plexmedia]
path=/var/lib/plexmedia
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Music]
path=/home/alan/Music
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/shared box is not a well formed usershare file.
info_fn: Error was Path is not a directory.

---

### Post by Morbius1 on 2012-08-22
What are the permissions along the entire path to Music? In other words:
```
ls -dl /home
ls -dl /home/alan
ls -dl /home/alan/Music
```If anywhere along that path it does not allow a remote guest ( in Linux terms it would be the same as "other" ) access then you will get a "failed to mount" error.

One way around this since you have created only guest or public shares is to make every remote guest appear to be you for samba shares. You would need to add another line to the [global] section - right around the workgroup line that looks like this:
```
force user = alan
```Then restart samba:
```
sudo service smbd restart
```[COLOR=Blue]

[COLOR=Black] Then see if the following command still gives you the error:[/COLOR]
[/COLOR]```
[COLOR=Blue] [COLOR=Black]gvfs-mount smb://basement/Music[/COLOR][/COLOR]
```
[COLOR=Blue]Side note[/COLOR]: I noticed that you preceded every command I asked you to run with sudo. Testparm and net usershare do not require it. Will it not run for you without sudo?

---

