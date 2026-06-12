---
title: "Samba/Network Issues"
date: 2012-12-08
forum: Networking &amp; Wireless
---

### Post by Dxh3378 on 2012-12-08
A Tale of Two Laptops:
I have an Acer notebook running Linux Mint with Samba.  
I also have a HP dv6 that dual boots Win7 and Ubuntu 12.04.
On the HP, while in Windows, the network is doing just fine, I can see all the folders that are marked to share.  The issue is when I am in 12.04.  What is strange is that works sometimes, but not others, but as of late, trying to connect to my server just causes the Browse Network to become unresponsive and require a force quit.

I've looked for solutions, but every thing that pops up once you mention Samba and Ubuntu in a search is about Windows issues, which I don't have.

Thanks for any assistance,
D

---

### Post by TheFu on 2012-12-08
What do the log files on the client AND on the server say?
Do other network connections methods, say ssh, work too?
Have you tried using smbclient (CLI version) with verbose set?

Basically, we need to determine if this is a samba issue or  an issue with the GUI tool that you are trying to use.

Looking at the log files is the first step. Those are usually in /var/log/samba/

---

### Post by Morbius1 on 2012-12-08
What would be helpful as a first step is to post the output of the following command from your 12.04 machine so we can all see how the samba client sees the network.
```
smbtree
```Depending on the output we may also need to see the output of these commands from the Linux server:
```
testparm -s
``````
net usershare info --long
```

---

### Post by Dxh3378 on 2012-12-08
FYI if you haven't guessed, I'm a total noob so please bear with me.

Ran the [smbtree] on the 12.04, it prompts me for a password, I thought I had configured Samba to not have one, but I guess that's not the case.  Anyhow, I have no clue what it is if I in fact set one up.

[testparm -s] output:

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[Myshare]"
Global parameter wins support found in service section!
NOTE: Service Myshare is flagged unavailable.
Processing section "[printers]"
Processing section "[print$]"
Processing section "[pc-3]"
Processing section "[test]"
WARNING: The security=share option is deprecated
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	netbios name = PC-3
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	encrypt passwords = No
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
	guest ok = Yes

[Myshare]
	comment = Myshare
	path = /myshare
	read only = No
	available = No

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

[pc-3]
	path = /home/pc-3

[test]
	path = /home/pc-3/test


[net usershare info --long] gives no output

---

### Post by Morbius1 on 2012-12-09
*** Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Find the following lines:
> security = SHARE
    encrypt passwords = NoAnd change it to this:
> security = USER
    encrypt passwords = Yes*** Add another line - right under the workgroup line in the [global] section:
```
name resolve order = bcast host lmhosts wins
```*** Change this:
> [Myshare]
    comment = Myshare
    path = /myshare
    read only = No
    available = NoTo this:
> [Myshare]
    comment = Myshare
    path = /myshare
    read only = No
    [COLOR=Blue]**#available = No**[/COLOR]*** Save smb.conf. Then restart your samba services:
```
sudo service smbd restart
sudo service nmbd restart
```Wait 5 minutes - seriously - 5 minutes. Then try to access your share.

---

### Post by Dxh3378 on 2012-12-09
Ok I edited the smb.conf file as suggested above.

Now when I click to browse network, I can see pc-3 as a server,(the little icon is there now) but when I click to open the shared folder I get this message
[DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered]

So I did the smbtree command again
[WORKGROUP
	\\PC-3           		pc3-Aspire-5517 server (Samba, Ubuntu)]

and then went ahead and ran the testparm again

[Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[Myshare]"
Global parameter wins support found in service section!
NOTE: Service Myshare is flagged unavailable.
Processing section "[printers]"
Processing section "[print$]"
Processing section "[pc-3]"
Processing section "[test]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	netbios name = PC-3
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
	name resolve order = bcast host lmhosts wins
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb
	guest ok = Yes

[Myshare]
	comment = Myshare
	path = /myshare
	read only = No
	available = No

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

[pc-3]
	path = /home/pc-3

[test]
	path = /home/pc-3/test    ]



I just checked the network again and I was able to navigate right to some files within the shared folders.
So It still seems to be hit or miss, but at least there seems to be some improvement.

Let me know what you think,
and thanks again Mo

---

### Post by Morbius1 on 2012-12-09
The "it works sometimes but not others" is perplexing. It may have something to do with this:
> [DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered]
Did a quick google search and found a bug report: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/386417](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/386417)

It's listed as Medium importance but still unresolved from 2009 even though there are posts from Ubuntu 12.04 in there. This is not encouraging. Let me dig around a little on this.

---

