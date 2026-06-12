---
title: "Setting up Samba"
date: 2011-08-16
forum: Networking &amp; Wireless
---

### Post by Phil Binner on 2011-08-16
I am trying to migrate from Windows to Ubuntu. Actually I have been trying this for several years now, and I have kept grinding to a halt after other work got in the way. This time I am using 11.04, and things are looking decidedly better. So fingers crossed.

I have Ubuntu installed on 3 machines, a desktop, a laptop and a netbook. Each of these is largely doing it's own thing independently but now I want them to work together, and also with the existing windows machines I'm trying to replace.  I've installed the Samba package in the laptop, but I haven't configured it yet. My first question is:

1. Do I have to install / configure Samba on each machine, or will one machine act as a server for the others.

I did actually manage to install Samba on an old machine a couple of years ago but, apologies to anyone who helped me then, I can't remember how I did it. It never did work very consistently, but I always had the feeling that it was Windows that was at fault rather than Ubuntu.  One thing I do think I remember, was that very little, if anything, had to be done to the smb.conf file. Once Samba was running it could be configured graphically. So my second question is:

2. Having installed Samba, can I just start it and then use a GUI to set it up. If the answer is yes, how do I start it and where is the GUI.

There seem to be a couple of workgroups left over from previous attempts at Ubuntu. If they were setup by Samba (??) then they only exist now as a memory in Windows.  One of my Windows machines is a member of one of these workgroups, but the windows machines are all Windows 7 now, so they don't use workgroups in the same way. I can connect to the machine that is a member, however, even though I can't even see the other Ubuntu machines.

Currently I'm struggling with a foreign language that includes words like "Daemon" and "meta-file". If anyone can help with simply worded advice I'll be everso grateful. 

Thanks in advance.

Phil Binner

---

### Post by Phil Binner on 2011-08-17
I've now tried to follow the setup instructions for Samba. I've edited the smb.config file and re-started Samba, but now I have less connection to the network than before. I can't see anything but myself.

The problem is I don't know what I'm trying to achieve with Samba (except to have access to the other machines and give them access to me). Without Samba I can see the windows machines on the network, but they can't see me. I can't see any other Ubuntu machine on the network, and they can't see me either.  Do I actually need Samba, or is this a red herring.

Below is the output of testparm on the edited smb.conf. This is followed by the restart instructions.


bigbin@Middlebin-Ubuntu:~$ testparm /etc/samba/smb.conf
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[share]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = LIBERTY HALL
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
	wins support = Yes
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[homes]
	comment = Home Directories
	read only = No
	create mask = 0775
	directory mask = 0775

[share]
	comment = Ubuntu file server share
	path = /srv/samba/share
	read only = No
	create mask = 0755
	guest ok = Yes
bigbin@Middlebin-Ubuntu:~$ sudo restart smbd
smbd start/running, process 3040
bigbin@Middlebin-Ubuntu:~$ sudo restart nmbd
nmbd start/running, process 3049


I note that the server mode is ROLE_STANDALONE.  Is this my problem, and if so what is causing it.

Thanks in advance.

Phil Binner

---

### Post by capscrew on 2011-08-17
> **Phil Binner said:**
> ...

I have Ubuntu installed on 3 machines, a desktop, a laptop and a netbook. Each of these is largely doing it's own thing independently but now I want them to work together, and also with the existing windows machines I'm trying to replace.  I've installed the Samba package in the laptop,
but I haven't configured it yet. 
What package did you install?  Did you do this through Synaptics?> 
My first question is:

1. Do I have to install / configure Samba on each machine, or will one machine act as a server for the others.
The basic Samba packages are installed by default.  This means any Ubuntu host should be able to browse the shares for files and folders (e.g. act as a client).  If you want an Ubuntu machine to hold files and share them with others then you need to install the Samba server portion.

Server = provides space for files and folders -- Client requests files and folders

Any Ubuntu host can be both a server and a client at the same time.  Or, if you wish,  just one of these. > 

... Once Samba was running it could be configured graphically. So my second question is:

2. Having installed Samba, can I just start it and then use a GUI to set it up. If the answer is yes, how do I start it and where is the GUI.

You should not have to *start *Samba.  It should be started automatically as Ubuntu boots up.  If you wish to create Samba shares using the GUI you can just right click on the folder you wish to share and look for *sharing options* on the menu.  Note: The first time you do this, you will be notified that the Samba server will be installed. > 

There seem to be a couple of workgroups left over from previous attempts at Ubuntu. If they were setup by Samba (??) then they only exist now as a memory in Windows.  One of my Windows machines is a member of one of these workgroups, but the windows machines are all Windows 7 now, so they don't use workgroups in the same way. I can connect to the machine that is a member, however, even though I can't even see the other Ubuntu machines.

Currently I'm struggling with a foreign language that includes words like "Daemon" and "meta-file". If anyone can help with simply worded advice I'll be everso grateful. 

Thanks in advance.

Phil Binner
Sometimes its useful to learn these terms.  It certainly makes it more precise when describing how the system works.  :-)

---

### Post by capscrew on 2011-08-17
> I have not been able to get the command
```
testparm -s /etc/samba/smb.conf.master > /etc/samba/smb.conf

```
to update the smb.conf, however, I get permission denied, or some such. I think I would have to log in as root to make this work, so I just updated smb.conf with sudo gedit instead. That would have prevented the change from being done.

Anyone know how I can get testparm to output the new file, i.e. how i get teh permission to work.


Output the file to a directory *you have write permissions to*, such as your home directory.  Then move (mv) or copy (cp) the file using sudo.  Or as you say you can login as root.  The reason you can't do it the way you are attempting to use is that the sudo is not preserved with the pipe (>).  You can do the first part but not the second part.

> Yes, but the problem is that I get the same symptoms. I can't see any other computers, Windows or Ubuntu, and they can't see me. Without Samba I can at least see the windows machines.

So are you are saying that you can browse the Windows shares without the Samba package (for the server)?   When you install the the Samba server you loose the ability to browse?

The basic samba client routines are installed by default (samba-common).

---

### Post by Morbius1 on 2011-08-18
Just noticed one thing which has an impact but doesn't necessarily fit all your symptoms:
> bigbin@[COLOR=Blue]Middlebin-Ubuntu[/COLOR]:~$ testparm /etc/samba/smb.conf
Load smb config files from /etc/samba/smb.confBy default samba will display the hostname to the rest of the network but samba  unlike Linux itself has rules attached to it. One is that it can only be 15 characters long. Yours is 16. The easiest way to correct this for samba purposes is to add the following line to the [global] section of smb.conf:
```
netbios name = middlebin-ubu
```*[COLOR=Blue]It doesn't have to be that exact name but it does have to be 15 characters or less in length. [/COLOR]*

You might want to check the rest of your Linux machines for the same issue and don't forget to restart samba:
```
 sudo service smbd restart
```

---

