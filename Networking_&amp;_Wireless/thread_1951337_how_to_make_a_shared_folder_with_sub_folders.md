---
title: "how to make a shared folder with sub folders"
date: 2012-04-02
forum: Networking &amp; Wireless
---

### Post by s1baker on 2012-04-02
hi,
I have a desktop with Ubuntu on it and I have a laptop with Win7 on it and the two are net-worked together with a wireless modem.

I have made a shared folder on my desktop to where I place files that I want to work on using either machine and transfer between the two machines.

Question:
When I transfer a folder from Ubuntu desktop ( that has a lot of sub folders and sub-sub folders in it ) to the shared folder that I have created, I cannot read-write to them using the Win7 laptop unless I go into the shared folder and set up the sharing option on each and every one of the sub-folders and sub-sub folders, etc.

Is there a way to set up the shared folder to where when one puts something into it, everything is "shared" without having to go through this time consuming process?

Thanks

---

### Post by dandnsmith on 2012-04-02
I can't be sure that I'm interpreting what you're saying correctly.

Talk of the desktop confuses me, particularly - are you meaning a PC, or the thing you see on the screen when you've logged on?

I don't have any problems with shared folders having a hierarchy - so I suspect that it is a question of permissions, and you need to look at the permissions on the sub-folders, and then ensure that the default permissions when you create them are what you thought you were getting.

Good luck

---

### Post by s1baker on 2012-04-02
The desktop computer is a just a regular PC box that is about 16" high that sits on my desk. It is the one that has Ubuntu ( 10.10 32 bit ) on it. It does not have a wireless card in it but is connected to my router with a ethernet cable. The laptop with Win7 is networked with the wireless router.
My shared folder that I want to use for common files is on my desktop ( the one with Ubuntu on it. )

---

### Post by Morbius1 on 2012-04-02
Why not post the output of the following commands so we can all see how you are set up:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by s1baker on 2012-04-02
here is testparm -s:

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
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

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

```


and here is net usershare info --long:

```
info_fn: file /var/lib/samba/usershares/jobs is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[forwin7]
path=/home/cody/forwin7
comment=
usershare_acl=Everyone:F,
guest_ok=y

```

---

### Post by Morbius1 on 2012-04-02
If "cody" can access all the files in "/home/cody/forwin7" locally then make the remote user on Win7 look like "cody":

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section - right under the workgroup line is where I'd put it:
```
force user = cody
```Then save smb.conf and in a terminal restart samba:
```
sudo service smbd restart
```Note: Every time smbd is restarted the network has a fit and it could take a few minutes for things to settle down before you can access the shares again.

**EDIT**: Sorry, I forgot you are using Lubuntu. I don't remember the default editor there so substitute that for the gedit reference I made above.

---

### Post by s1baker on 2012-04-02
I don't think I have samba, do I need it to share a folder between the two computers?

this in terminal :$ samba -help
gives this:

```
The program 'samba' is currently not installed.  You can install it by typing:
sudo apt-get install samba4
```

---

### Post by Morbius1 on 2012-04-02
You have samba installed or else you would not have been able to create this samba share:
> [forwin7]
path=/home/cody/forwin7
comment=
usershare_acl=Everyone:F,
guest_ok=y
And whatever you do don't install samba4 !!!

---

### Post by s1baker on 2012-04-02
It seems to be working now, I seem to be able to copy over files in the shared folder with all the inclusive sub-folders. I will try it out and see if all works like I want it to. Also, in my very first post, I made a bobo.

Instead of ```
"net-worked together with a wireless modem"
```
 I meant to say ```
"net-worked together with a wireless router"
```

Also, I have Ubuntu 10.10 running on the desktop.

---

