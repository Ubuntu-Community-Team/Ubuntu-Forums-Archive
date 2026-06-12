---
title: "Unable to mount location - failed to mount Windows share"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by GaryReggae on 2011-07-30
I am having problems sharing my external hard drive.

It is plugged into my Ubuntu LTS media centre computer and is just a standard USB Seagate HDD. It works fine when I access it from the same computer it is plugged into, both in Ubuntu and Windows machines.

I have set it up as a shared resource using the shares-admin app and at the same time, shared the home folder of that machine. I can access the home folder fine from my laptop over the network but when I try to access the external HDD, I get the following error msg: 'Unable to mount location - failed to mount Windows share'.

My laptop has the same OS as the media centre - Ubuntu LTS 10.04 Lucid. I am trying to access the share via Places > Network. I'm not sure why it comes under Windows shares because neither machine has Windows on. The network is a Wi-fi home network.

Please let me know if you need any further information. Hopefully, there is a simple solution to this.

Thanks,

Gary

PS: I just tried to access it from a Windows machine and that says that the network is not acceible. It opens the home folder fine though, as with the laptop.

---

### Post by GaryReggae on 2011-08-01
Any suggestions folks? If I can't get this sorted then my computer is totally useless for the purpose I bought it as sharing that drive over the network is crucial.

The only option would be to use Windoze...and that's not a route I want to go down.

I have searched this forum and not found anything that seems to be relevant.

---

### Post by parabol2112 on 2011-08-01
I suppose this won't help you much, but I'm having the exact same issue with my home network.  I've read that Samba is only configured to be able to share things on the Filesystem.  It could also be a disk mounting problem.  

It looks like there's some info about editing smb.conf in this tutorial here: [http://ubuntuforums.org/showthread.php?t=1740312](http://ubuntuforums.org/showthread.php?t=1740312)

Alas, it's mostly for dealing with Ubuntu/Windows configuration issues.

Also, the answer might be buried somewhere in the Samba manual:
[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/)

It's not much, but let me know if you can figure out how to share folders on a USB drive.

---

### Post by Morbius1 on 2011-08-01
> I have set it up as a shared resource using the shares-admin app and at the same time, shared the home folder of that machine.I didn't think shares-admin still worked. Anyway, if you open up your /etc/samba/smb.conf file you should see at the bottom the share definition. Generically it looks something like this:

> [share-name]
comment = 
path = /media/some-name
read only = No
guest ok = yesWhat you want to do is add a "force user" line to that share definition so that the remote user appears to be you:
> [share-name]
comment = 
path = /media/some-name
read only = No
[COLOR=Blue]force user = your-user-name[/COLOR]
guest ok = yesThen restart samba:
```
sudo service smbd restart
```If you run into problems post the output of the following command:
```
testparm -s
```

---

### Post by numeroususr on 2011-11-06
Confirmed this fixes the problem (or at least it did for me). As soon as I add this to any new share I create it works. Also, not sure if this is important but my user name in windows and linux match.

---

### Post by baditaflorin on 2012-05-05
Ubuntu 12.04 . Problem not fixed

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = 1000
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

---

### Post by Morbius1 on 2012-05-05
> Ubuntu 12.04 . Problem not fixed
For one thing you don't have anything to share.

Maybe you created a Samba Usershare?
```
net usershare info --long
```

---

### Post by baditaflorin on 2012-05-09
I must have something to share ? 

Important is for me to acces other computers, not share something from the ubuntu laptop.

I don`t know what to post, what would be helpfull 

badita@vivi:~$ net time
Can't contact server (null). Error NT_STATUS_BAD_NETWORK_NAME

---

### Post by baditaflorin on 2012-05-09
> **Morbius1 said:**
> For one thing you don't have anything to share.

Maybe you created a Samba Usershare?
```
net usershare info --long
```

Imposible, imposible, too complicated;.

And the name of the windows Workgroup is 1000, the computers that have Windows XP and the computers wioth Windows 7 i don`t know. But they all can acces all that they want, without even thinking , typing, or command promoting somethiong, serching on google, posting on 1 years post of mine,etc and still not to be able to use, and be afraid if i get it to work to upgrade to a newer version of ubuntu, because all can crash like a domino efect.

I cannot install ubuntu on 5 computers, because wine cannot emulate 1 windows program that is use for tranzactions.

And second, because i cannot garantee that the Windows Sharing, printers, etc will work. 
This is just sad. i love ubuntu, but ubuntu gets me frustated.

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = 1000
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
badita@vivi:~$

---

### Post by baditaflorin on 2012-05-09
> **Morbius1 said:**
> For one thing you don't have anything to share.

Maybe you created a Samba Usershare?
```
net usershare info --long
```

And on this i don`t get any response :(

badita@vivi:~$ net usershare 
Invalid command: net usershare 
Usage:
net usershare add             Add/modify user defined share
net usershare delete          Delete user defined share
net usershare info            Display information about a user defined share
net usershare list            List user defined shares
badita@vivi:~$ net usershare info
badita@vivi:~$ net usershare infolist
Invalid command: net usershare infolist
Usage:
net usershare add             Add/modify user defined share
net usershare delete          Delete user defined share
net usershare info            Display information about a user defined share
net usershare list            List user defined shares
badita@vivi:~$ net usershare list
badita@vivi:~$ net usershare add
net usershare add [-l|--long] <sharename> <path> [<comment>] [<acl>] [<guest_ok=[y|n]>]
	Adds the specified share name for this user.
	<sharename> is the new share name.
	<path> is the path on the filesystem to export.
	<comment> is the optional comment for the new share.
	<acl> is an optional share acl in the format "DOMAIN\name:X,DOMAIN\name:X,...."
	<guest_ok=y> if present sets "guest ok = yes" on this usershare.
		"X" represents a permission and can be any one of the characters f, r or d
		where "f" means full control, "r" means read-only, "d" means deny access.
		name may be a domain user or group. For local users use the local server name instead of "DOMAIN"
		The default acl is "Everyone:r" which allows everyone read-only access.
	Add -l or --long to print the info on the newly added share.
badita@vivi:~$

---

### Post by Morbius1 on 2012-05-09
**First**, The original post concerned creating a share on Linux:
> I am having problems sharing my external hard drive.

It is plugged into my Ubuntu LTS media centre computer and is just a  standard USB Seagate HDD. It works fine when I access it from the same  computer it is plugged into, both in Ubuntu and Windows machines.**Second**, your entire first post was:
>          Ubuntu 12.04 . Problem not fixed**Third**, Now we learn that:
> Important is for me to acces other computers, not share something from the ubuntu laptop.
This thread is almost a year old and your question is unrelated to the topic. I suggest you start a separate topic.
[COLOR=Blue][B]
As a side note[/B][/COLOR]: If someone suggest running a particular command like this for example:
```
net usershare info --long
```Running the following is not the correct response:
> badita@vivi:~$ net usershare 

---

### Post by baditaflorin on 2012-05-10
> **Morbius1 said:**
> **First**, The original post concerned creating a share on Linux:
**Second**, your entire first post was:
**Third**, Now we learn that:
This thread is almost a year old and your question is unrelated to the topic. I suggest you start a separate topic.
[COLOR=Blue][B]
As a side note[/B][/COLOR]: If someone suggest running a particular command like this for example:
```
net usershare info --long
```Running the following is not the correct response:

Yeah, i know :) Sorry, i hate when stuff don`t work :)

I tried this as well, but no feedback badita@vivi:~$ net usershare info --long
badita@vivi:~$ net usershare info
badita@vivi:~$ net usershare info
badita@vivi:~$ 

But the good thing that now it`s working :) I can see other computers and all :)

Love Ubuntu and this great community :)

---

### Post by 25 minutes on 2012-05-18
i've just installed ubuntu 12.04 for 2 days. And i have the same problem. I can not connect to windows share. I can't see the file smbd.conf in /etc/init/ . Help me to solve it!

---

### Post by StSav012 on 2012-06-26
> **25 minutes said:**
> I can't see the file smbd.conf in /etc/init/ .
The file is located in /etc/samba/.

---

### Post by Morbius1 on 2012-06-26
> **25 minutes said:**
> i've just installed ubuntu 12.04 for 2 days. And i have the same problem. I can not connect to windows share. I can't see the file smbd.conf in /etc/init/ . Help me to solve it!
The file: **/etc/init/smbd.conf **is an upstart configuration file that starts the samba server on startup. If you haven’t installed the samba package then it won't be there. If the only thing you want to do is connect to another host's shares then you don't need the samba package. That's for creating shares on your own machine for others to access.

[COLOR=Blue]*As a side note*[/COLOR]: Even if you hadn't installed the samba package there is still a samba configuration file at: **/etc/samba/smb.conf**. That file is used by the samba client as well as the samba server.

---

### Post by humancomp on 2013-01-12
I sort this problem creating a group call admin:

```
sudo groupadd admin
```

Check that the admin group is part of the sudoers:

```
sudo cat /etc/sudoers
```

Now you add your user to the admin group :
```

sudo usermod -aG admin username
```

you can check if your user is part of the group :

```
sudo cat /etc/group | grep '^admin'
```

this worked for me

---

### Post by progone on 2013-01-20
Try using 'dolphin' instead of nautilus to access your network and windows pc

---

