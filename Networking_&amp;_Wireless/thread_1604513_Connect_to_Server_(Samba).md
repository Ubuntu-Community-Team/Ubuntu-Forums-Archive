---
title: "Connect to Server (Samba)"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by rob150588 on 2010-10-24
Hi There.

I'm having a bit of a problem connecting to a Samba share on 10.04.

I started off by installing smbclient and smbfs as I've done before, but this time is was giving me an error saying that libwbclient0 was already installed with a newer version (can't remember the exact error, this was yesterday and I've slept since then).

So I uninstalled libwbclient0 then installed smbfs and smbclient which resolved libwbclient0 as an unistalled dependency.

However, now when I go to "Connect to server", the only option listed is "Custom Location". Tried connecting to the server with the "smb://servername" address...no joy.

Saw a couple of threads with a similar problem, but they were refering to gvfs-backends being reinstalled and reinstalling Nautilus. Tried both those options and am still failing.

Help please ?

Cheers.

---

### Post by officerdibble on 2010-10-24
Had similar problem with a new install of 10.10 on a new machine. Problem was I could not see any network connected machines. In my case I have a server running on the default computer name given by the setup process, ie. andy-desktop, this name was duplicated on the new 10.10 set up, and therefore conflicted.

I simply renamed both /etc/hostname and /etc/hosts to something different from the name of my other machine and hey presto! I used 'sudo gedit /etc/hostname' changed the name, saved, done the same with /etc/hosts and restarted.

---

### Post by rob150588 on 2010-10-24
Thanks for your reply.

I had a look at the hosts and hostname files. They were all in order and not conflicting with another machine...changed them anyway just to make sure. But still no joy.

I think I may have broken something on a different level when I was installing the Samba system...

---

### Post by arju305 on 2010-10-24
Guys I am having a problem with samba.
firstly i installed it :
$sudo apt-get install samba
$sudo apt-get install system-config-samba
then i restarted the server.
from administrator-> samba i customized it for access to every one.
I found that.
from my ubuntu, I could access windows 7
but from windows 7 I cannot access ubuntu.
need your help.
Thanking you in advance.
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=10019153") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=10019153")

---

### Post by rob150588 on 2010-10-24
Hi Arju305.

Probably not the right thread for the question. But I'll have a go at it.

May be an issue with the filing system ? Ubuntu can access a plethora of FS's (NTFS, FAT, and a load of others).

Whereas (as far as I'm aware), Windows is a little more selective and won't be able to access the Ubuntu ext3 (or ext4) filing system.

This may help you:

[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

---

### Post by rob150588 on 2010-10-24
UPDATE:

Not completely solved, but have mounted the Samba share automatically by editing the fstab for mount on startup.

---

### Post by arju305 on 2010-10-24
> **rob150588 said:**
> UPDATE:

Not completely solved, but have mounted the Samba share automatically by editing the fstab for mount on startup.


I am trying to access ubuntu files from windows 7 through networking. I can access 7 through ubuntu but not opposite.
the shared folder is seen by windows but when ever i double clik it...... it shows "windows cannot access"

---

### Post by luisloboborobia on 2010-12-09
My problem got solved running 

```
sudo apt-get install gvfs-backends
```

---

