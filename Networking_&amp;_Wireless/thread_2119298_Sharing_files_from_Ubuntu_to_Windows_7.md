---
title: "Sharing files from Ubuntu to Windows 7"
date: 2013-02-23
forum: Networking &amp; Wireless
---

### Post by Agent.Logic_ on 2013-02-23
Hi,

I'm trying to share files from my Ubuntu 12.04 computer to my Windows 7 computer with samba. I am able to access all Windows shares on my Ubuntu PC, but not the other way around.

I can see my Ubuntu computer name in the Windows 7 Network menu, but when I click on it, it gives an error saying "Windows cannot access \\EREBUS. Check the spelling of the name. Otherwise there might be a problem with your network..." (the Ubuntu computer is named "Erebus"). I can even manually type the IP address of my Ubuntu PC in the windows explorer address bar and see all the shares. It seems that the name is not resolving to its IP address. How can I fix that?

---

### Post by drdos2006 on 2013-02-23
Hi there

See this thread.

[http://ubuntuforums.org/showthread.php?t=1981511](http://ubuntuforums.org/showthread.php?t=1981511)

regards

---

### Post by Agent.Logic_ on 2013-02-24
Perhaps I should explain the problem better. The file sharing works fine between both the computers. The only problem is, on Windows 7 (named "Valhalla"), I see my Ubuntu laptop's machine name (named "Erebus") in the "Network" menu, but clicking on it displays an error message (see first attachment).

The Ubuntu laptop is on a WiFi network, and the Windows 7 desktop is a wired desktop machine. Both computers are in the same workgroup, but the only way I can access all the Ubuntu shares is by manually typing its IP address in Windows Explorer (see second attachment). I'm thinking this is because the name "Erebus" is not resolving to its IP address. How do I fix this minor issue, so that I don't have to type "Erebus'" IP address every time I want to access the shared files on "Valhalla"?

---

### Post by tjsummers51l on 2013-02-24
I had a similar issue on my network.  I just put the ip and machine name in the host file on each computer.  Old school, but effective.

---

### Post by Agent.Logic_ on 2013-02-24
@tjsummers51l: Yeah, I'm keeping that as a last resort :D. I'm just looking for a convenient solution :D. I followed the steps in [this]("http://www.liberiangeek.net/2012/10/share-files-between-windows-7-and-ubuntu-12-10-quantal-quetzal/") article, and apparently it should be straightforward after the setup is complete.

---

### Post by Morbius1 on 2013-02-24
Edit smb.conf and under the workgroup line add the following:
```
name resolve order = bcast host lmhosts wins
```Then restart samba in this order:
```
sudo service smbd restart
sudo service nmbd restart
```If that doesn't fix it please post the output of the following:
```
testparm -s
smbtree
```

---

### Post by Agent.Logic_ on 2013-02-24
Hi Morbius1, thanks for taking your time to reply!

Made that change to smb.conf, but the hostname still does not resolve.

> **Morbius1 said:**
> please post the output of the following:
```
testparm -s
smbtree
```

```
agentlogic@Erebus:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[eBooks]"
Loaded services file OK.
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
	name resolve order = bcast host lmhosts wins
	dns proxy = No
	usershare allow guests = No
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

[eBooks]
	path = /home/agentlogic/Documents/eBooks
	valid users = agentlogic
	read only = No
```

```
agentlogic@Erebus:~$ smbtree
Enter agentlogic's password: 
WORKGROUP
	\\VALHALLA       		
	\\EREBUS         		Erebus server (Samba, Ubuntu)
		\\EREBUS\print$         	Printer Drivers
		\\EREBUS\eBooks         	
		\\EREBUS\IPC$           	IPC Service (Erebus server (Samba, Ubuntu))

```

---

### Post by Morbius1 on 2013-02-24
Unfortunately there doesn't seem to be anything wrong with your set up.

Smbtree would have given you all sorts of errors if it were the usual suspects of firewall, nmbd service not running, etc...

These 2 machines are in the same subnet right? They are all 192.168.0.xxx or whatever your base ip addresses are? Browsing by name doesn't work across subnets.

---

### Post by gordintoronto on 2013-02-24
Perhaps this is an upper-and-lower case issue. I only use lower case when naming my computers, and folder sharing "just works."

---

### Post by Agent.Logic_ on 2013-02-25
@Morbius1: Yeah, the Windows 7 desktop is 192.168.1.100 and the Ubuntu laptop is 192.168.1.101, I've assigned them permanent IP addresses. Does it matter that one PC is wired and the other is on WiFi?

@gordintoronto: Perhaps, but I'm able to access all Windows 7 shared folders on Ubuntu, and that PC is named "Valhalla", with a capital V.

@both: I tried pinging the hostname from both computers, and they both complain about an unknown host when pinging the other computer. They can ping themselves, and it apparently doesn't matter how I spell them: erebus/Erebus/EREBUS and valhalla/Valhalla/VALHALLA all resolve to localhost and ping successfully.

**EDIT:** Adding the IP and machine name in the hosts file works, like tjsummers51l pointed out in an earlier post. But I still wonder why it doesn't work "out of the box"...

---

