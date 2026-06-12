---
title: "Samba security Bug??"
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by Derek Karpinski on 2011-06-24
I have Samba set up to show the /home folders to the other computers in the network.  From our Win7 laptop, our homes show up if we are logged in (in windows) under the same user as the ubuntu 'server'.  As far as I can tell, these folders get mounted when the user logs into windows, with the password that is used to log in to the windows acct.
 
I have installed on my android phone 'file expert'.  My samba shared /home shows up on the network, as I would expect, but requires no user name or password to browse it's contents!  I can even browse the contents on my wife's phone.
 
I would think that this share should be password protected just as I see it on the windows side.  If my wife logs into windows, she can see her home, and mine, but she can't get into mine.
 
BTW, I have encrypted homes.
 
Any ideas?

---

### Post by Morbius1 on 2011-06-24
Please post the output of the following command from the Samba "server":
```
testparm -s
```
And just in case:
```
net usershare info --long
```

---

### Post by Derek Karpinski on 2011-06-24
When I get home, I will post ASAP.:)

---

### Post by Derek Karpinski on 2011-06-24
```
derek@home-pc:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Public]"
Processing section "[Quicken Backup]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
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

[homes]
	comment = Home Directories
	read only = No
	create mask = 0700
	directory mask = 0700
	hide files = /desktop.ini/$RECYCLE.BIN/
	browseable = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Public]
	path = /mnt/Windows/Users/Public
	valid users = derek, shani
	read only = No

[Quicken Backup]
	path = /mnt/ExternalHDD/Quicken Backup
	valid users = derek, shani
	read only = No

```

And I got no results from:

```
net usershare info --long
```

---

### Post by Morbius1 on 2011-06-25
Here's my theory - and by the way I don't have an android phone so there is no way for me to verify this:

I looked up "file expert" and I can't find out much about it except it does say that it can act as an "smb client". There's two ways to implement an smb client - The Windows way and the Linux way. 

Windows has two 14 year old design flaws one of which is it passes the Windows user's actual local login user name and password when it browses for shares. If the local Windows login user name and password matches exactly the Samba servers user name and samba password then the Windows client is allowed access to private shares. The Windows user never gets prompted for authentication since it's already been passed without the users knowledge. The second flaw is that once a successful connection is made it remembers the user name and password that made that possible and remembers it forever - also without your knowledge.

My theory is that "File Expert" is relying on one of these mechanisms to make a connection. It's not that credentials are not required it's that it's being sent without your knowledge.

Easy enough to find out if I'm right and that's to change the samba password on the Linux server. So if derek is one of the users that the android machine has access to without a password prompt then change derek's samba password to something different:
```
sudo smbpasswd -a derek
```Then give it something like morbiustest

Then see if android still has access.

---

### Post by Derek Karpinski on 2011-06-25
```
sudo smbpasswd -a derek
```

And I changed it too 'morbiustest'.

I have no access to the samba shares from Android.  Funny, because I never remember putting in a password in file expert when I installed it.

So, I guess things are 'working as designed'?  So, now how do I change it back?  Just enter my old password?

---

### Post by Derek Karpinski on 2011-06-25
I changed it back, and found the setting in file expert to change the login name and password.

Everything is working fine now.

Thanks for all your help! :KS

Now, if I could just figure out how to decrypt /home folders without the user being logged in on the 'server', things would be great.  I know Samba can kick off scripts when a user connects.  Could I run the decrypting scripts whenever a user connects?

Either way, I'll marked this solved.

---

### Post by Morbius1 on 2011-06-25
> So, now how do I change it back?  Just enter my old password?
Yes just rerun the "sudo smbpasswd -a derek" command with your old samba password.

---

### Post by capscrew on 2011-06-25
I use "valid users = %S" in my [homes] share. This plus "browseable = no" show keep others from seeing or being able to view your home directory.  Of course proper Linux file permissions on the directory is assumed.  My [homes] share looks like this (partially)```
[homes]
	comment = Home Directories
	browseable = no 
	guest ok = no
	valid users = %S
```

The documentation on valid users is illuminating```
valid users (S)

This is a list of users that should be allowed to login to this service.
Names starting with '@', '+' and '&' are interpreted using the same 
rules as described in the invalid users parameter.

If this is empty (the default) then any user can login. If a username is
in both this list and the invalid users list then access is denied for
that user.
[COLOR="SeaGreen"]
The current servicename is substituted for %S[/COLOR]. This is useful in 
the [homes] section.

[COLOR="Red"]Default: valid users = # No valid users list (anyone can
login)[/COLOR]

```
When no valid users parameter is declared the default is used ;-)

---

