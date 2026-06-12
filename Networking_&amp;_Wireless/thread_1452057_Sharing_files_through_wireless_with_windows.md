---
title: "Sharing files through wireless with windows"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by ki4jgt on 2010-04-11
I just purchased a wireless router, b/c my two computer's wouldn't adhoc, so how do I get them to share files now? 1 is ubuntu and the other is windows xp

---

### Post by spiky001 on 2010-04-11
you have to install samba hope this gets you up and running

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by ki4jgt on 2010-04-11
Already did

---

### Post by Morbius1 on 2010-04-11
Why not post the output of the following commands so we can see how things are set up on your linux machine:

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**
Type** testparm -s**
Type **smbtree**
Type **findsmb**
Type** nmap -sT 192.168.0.100/22**
[COLOR=Blue]*Change 192.168.0.100 to the ip address of the machine you're using.*[/COLOR]

You may not have nmap installed but when you issue the nmap command it will ask you if you want to install it - you do. Once it's installed run the nmap command again.

---

### Post by ki4jgt on 2010-04-11
```
jesse@Remember:~$ net usershare info
[downloads]
path=/home/jesse/Downloads
comment=
usershare_acl=Everyone:F,
guest_ok=y

jesse@Remember:~$ sudo net usershare info
[sudo] password for jesse: 
jesse@Remember:~$ sudo net usershare info
jesse@Remember:~$ testparm -s
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
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
jesse@Remember:~$ smbtree
Enter jesse's password: 
jesse@Remember:~$ smbtree
Enter jesse's password: 
findjesse@Remember:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
jesse@Remember:~$
``` 

I don't have my machines IP

---

### Post by Morbius1 on 2010-04-12
**net usershare info** shows that you have a valid share on your Linux box.
**testparm -s** shows that you have what looks like a valid default samba config file.

The problem is **smbtree** and **findsmb** indicates that you do not have any shares or even any machines on your network.

nmap would have made that more explicit. To find the ip address of your Linux machine:

Open **Terminal**
Type **ifconfig**

Somewhere in the output should be a line that looks like this:
> inet addr:192.168.0.100That's your Linux ip address. By issuing a:
```
nmap -sT 192.168.0.100/22
```It will list all the machines by ip address and all open ports on those machines.

It's hard to determine the problem at this point but my first guess is a firewall is in the way. On Windows disable it. On Linux, if you have enabled the firewall and added any rules, disable it. If you haven't touched the firewall then the default setup is fine and does not need to be altered. Once you've done that see if you can connect. If not run the smbtree, findsmb, and nmap commands again.

---

### Post by ki4jgt on 2010-09-02
Sorry for taking so long to get back to you, I'm in and out of my current location a lot, anyway, I've run nmap and ettercap on Ubuntu and all I see is the router.

---

