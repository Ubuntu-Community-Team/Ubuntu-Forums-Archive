---
title: "Failed to retrieve share list from server"
date: 2012-04-05
forum: Networking &amp; Wireless
---

### Post by Ifaistos on 2012-04-05
Hello everyone :-)

I have this problem for quite some time now.
Although I had managed somehow to have networking with my other two computers running Win7, about two upgrades ago, ever since I upgraded to 10.10 it seems that I "broke" smt and I haven't been able to fix it since then.

So I can't print from Linux or share files.  I have been able to live with it for quite some time, but I think that it is time that I attack this problem again.

Maybe there is a new way to fix it that is much easier.
I have tried almost everything there was on the net, but with no result.

Can anyone point me to a link with a definite solution to this problem, with specific, simple and step by step instructions?

I have installed samba and it was working fine about a year ago...

Thank you all in advance

---

### Post by miguelpires on 2012-04-05
> **Ifaistos said:**
> Hello everyone :-)

I have this problem for quite some time now.
Although I had managed somehow to have networking with my other two computers running Win7, about two upgrades ago, ever since I upgraded to 10.10 it seems that I "broke" smt and I haven't been able to fix it since then.

So I can't print from Linux or share files.  I have been able to live with it for quite some time, but I think that it is time that I attack this problem again.

Maybe there is a new way to fix it that is much easier.
I have tried almost everything there was on the net, but with no result.

Can anyone point me to a link with a definite solution to this problem, with specific, simple and step by step instructions?

I have installed samba and it was working fine about a year ago...

Thank you all in advance

Hi,
Same problem, 5 UBUNTU computers, 1 samba share and i can't see via nautilus the network... A few days ago, i can see all my computers. Any Idea?
Regard's
Miguel

---

### Post by Ifaistos on 2012-04-07
bumpity bump :-)

---

### Post by Ifaistos on 2012-04-07
Bump...

There must be smting that we could do !

---

### Post by roelforg on 2012-04-08
My 11.10 runs it's samba fine.
Maybe check your samba conf and if it has updates.
Also, i advise to have your server share the samba share directory over nfs,
lot faster and doesn't need samba as the kernel does it

---

### Post by Ifaistos on 2012-04-08
Thank you for your answer....

Could you please explain how do I do what you are suggesting?

Do you believe that this advice will make samba work, or just go faster??

---

### Post by Ifaistos on 2012-04-09
Bump?

---

### Post by Ifaistos on 2012-04-13
bump

---

### Post by Morbius1 on 2012-04-13
You are going to have to provide some information for people here to work with. Please post the output of the following commands:
```
testparm -s
``````
net usershare info --long
``````
hostname
```[COLOR=Blue]EDIT: And one more that I forgot:[/COLOR]
```
smbtree
```

---

### Post by Ifaistos on 2012-04-16
Thank you for the interest !!
Here is what you asked :-)

=====================================================
evans@DeepBlack:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[netlogon]"
Processing section "[profiles]"
Processing section "[printers]"
Processing section "[pdf-documents]"
Processing section "[pdf-printer]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
	workgroup = VASTNET
	server string = Samba file and print server
	interfaces = 127.0.0.1/8, 192.168.0.0/24
	bind interfaces only = Yes
	update encrypted = Yes
	client schannel = No
	server schannel = No
	allow trusted domains = No
	obey pam restrictions = Yes
	guest account = smbguest
	passwd program = /usr/bin/passwd '%u'
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	passwd chat timeout = 120
	username map = /etc/samba/smbusers
	password level = 6
	username level = 6
	unix password sync = Yes
	log file = /var/log/samba/samba.log
	max log size = 1000
	name resolve order = wins lmhosts bcast
	client signing = No
	client use spnego = No
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = cups
	machine password timeout = 120
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	delete user script = /usr/sbin/userdel '%u'
	add group script = /usr/sbin/groupadd '%g'
	delete group script = /usr/sbin/groupdel '%g'
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	logon script = %G.bat
	logon path = \\%L\profiles\%u
	logon drive = m:
	logon home = \\%L\homes\%u
	os level = 33
	local master = No
	domain master = No
	dns proxy = No
	remote announce = 192.168.0.255
	remote browse sync = 192.168.0.255
	idmap uid = 16777216-33554431
	idmap gid = 16777216-33554431
	template shell = /dev/null
	winbind separator = @
	winbind cache time = 360
	winbind use default domain = Yes
	winbind trusted domains only = Yes
	winbind nested groups = No
	winbind nss info = no
	hosts allow = 127., 192.168.0.
	cups options = raw
	follow symlinks = No

[homes]
	comment = Home Directories
	path = /home
	read only = No
	locking = No
	strict locking = No

[netlogon]
	comment = Network Logon Service
	path = /home/netlogon
	locking = No
	strict locking = No

[profiles]
	comment = User Profiles
	path = /var/samba/profiles
	read only = No
	create mask = 0600
	directory mask = 0700
	browseable = No
	locking = No
	strict locking = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	printable = Yes
	browseable = No
	locking = No
	strict locking = No

[pdf-documents]
	comment = Converted PDF Documents
	path = /home/pdf-documents
	read only = No
	guest ok = Yes
	locking = No
	strict locking = No

[pdf-printer]
	comment = PDF Printer Service
	path = /tmp
	guest ok = Yes
	printable = Yes
	printing = bsd
	print command = /usr/bin/gadmin-samba-pdf %s %u
	lpq command = 
	use client driver = Yes
==============================================================

net usershare info --long
[120gb(db)]
path=/home/evans/120Gb
comment=
usershare_acl=Everyone:R,DEEPBLACK@evans:F,
guest_ok=n

================================================================
evans@DeepBlack:~$ hostname
DeepBlack
================================================================
evans@DeepBlack:~$ smbtree
\Enter evans's password: 
evans@DeepBlack:~$ 
================================================================

---

### Post by Morbius1 on 2012-04-16
My very first recommendation if for you to tape a small note to your monitor as a reminder if you ever install a newer version of Ubuntu with the following words:
> Do not install gadmin-sambaIt may very well be that many of those parameters are harmless but it would take some time to compare it to the defaults to find out so if it were me I'd start over with a factory fresh copy of smb.conf. You can do it this way:

Rename your current file:
```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.bak
```Copy a backup smb.conf to the /etc/samba location:
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba
```Then edit the file as root:
```
gksu gedit /etc/samba/smb.conf
```Find the following line:
> encrypt passwords = no[COLOR=Blue]*It may list it as False*[/COLOR]
And change it to Yes:
> encrypt passwords = [COLOR=Blue]**yes**[/COLOR][COLOR=Blue]**EDIT**: As long as you are editing the file make one more addition to the [global] section - right under the workgroup line:[/COLOR]
```
 name resolve order = bcast host lmhosts wins
```Then restart samba:
```
sudo service smbd restart
```You may need further modifications but this will get you back to the default setup.

---

### Post by Ifaistos on 2012-04-16
It works !!!!

I don't know why, or how, but it works!!!

The only thing that I did more was to change the workgroup name into the workgroup that I am using!!

THANK YOU !!!

I have also stuck the post-it on my screen, so that I don't forget not to install gadmin-samba ;-) when I upgrade into 12.04

btw...

Could you please (if I am not asking too much) explain what these two lines that I added into the smb.conf file are doing?

THANK YOU AGAIN !!!

---

### Post by Morbius1 on 2012-04-16
I have no idea why the backup smb.conf in /usr/share has "encrypt password" set to no since Linux and Window are expecting it to be and won't work without it.

As for name resolve order, it's a sequence of steps Linux ( Windows goes through a similar process ) will take in order to convert or map a host name to an ip address. The default is:
> name resolve order = lmhosts wins host bcastBy default lmhosts doesn't exist, wins refers to a WINS server that you and most folks don't have set up in their LANS, and host refers to the hosts file that doesn't have any samba related stuff in there. That leaves bcast or broadcast that Windows also uses and it's the only mechanism that works by default in Ubuntu. I simply rearranged the order to put bcast first to lessen the chance for something to go wrong.

---

### Post by Ifaistos on 2012-04-16
hm... it worked for a while... but now it doesn't :(

I can't see the shares...

If I insist and refresh many times, I can see the shares, but I can't "get in" those folders.

Could it be windows blocking me?
Why didn't they block me before?

I even managed to add a printer and print some test pages... which worked just great!

Edit :

To be more precise : 
I click on Windows Networks and I don't see anything.  I go back, and do it again.  After a couple of times I can see the VASTNET which is the homegroup of the windows network.  Sometimes it tells me that it cannot open some of the folders and that I have to choose another application in order for me to "open" the file.  I then retry and choose the "Files" application and it opens it.

It seems that it works at the end, but with some delay or "twicking".  Is there a way I could fix that?

---

### Post by Morbius1 on 2012-04-16
I have to shut down for the day , sorry.

I can't think of anything more you can do on the Linux end of this situation. If you restart the smbd service this type of thing can happen because the network has to reset itself so for a few minutes nobody can see anything but if you are not restarting smbd then I'm not sure what's going on there on the Windows end.

---

### Post by Ifaistos on 2012-04-17
I do understand what you are saying.

You help was invaluable :-)
At least now it works...  I might have to "work" at it.. but at least it works.


Thank you for all your efforts!
I will mark this thread solved.

---

