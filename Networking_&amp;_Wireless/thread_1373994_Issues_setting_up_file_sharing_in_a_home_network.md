---
title: "Issues setting up file sharing in a home network"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by bobbyhenery on 2010-01-06
If anyone has any insight this would be very helpful for me... I have a home network with two desktops and I also have a netbook. The netbook and nettop (desktop) both run UNR 9.10 and my other desktop runs Ubuntu 9.10 with all updates in place. So all 3 machines are hooked up to my home network via wireless router (secure and password protect). I want to set up file shares between machines in order to move files between machines and also to have all machines connected to and accessing one shared printer. Fair enough. According to Ubuntu help I click on a folder, then properties then the share tab and click all checkboxes and give the share a name. Then I do likewise on my two other machines. So in theory once every machine has a share setup then you should be able to access via the other machines by simply going into Network, finding the machine, opening it and mounting the shared folder. In some cases I see the other machines but when I click to open them it says "unable to mount location". So now I would like to ask... where should I look to resolve this? The wireless router settings? Some type of network or security settings on each of my machines? If someone could guide me to troubleshoot this, that would be lovely.

---

### Post by Morbius1 on 2010-01-06
I always like to start with some basic "discovery" commands that will tell me the state of my network. Post the output of the following commands from one of the machines you are trying to access:

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**
Type **testparm -s**
Type **smbtree**
Type **findsmb**
Type **nmap -sT 192.168.0.100/22**
[COLOR=Blue]*Change 192.168.0.100 to the ip address of the machine you're using.*[/COLOR]

[COLOR=Blue]You may not have nmap installed but when you issue the nmap command it will ask you if you want to install it - you do. Once it's installed run the nmap command again.[/COLOR]

---

### Post by bobbyhenery on 2010-01-06
robbie@robbie-laptop:~$ net usershare info
[documents]
path=/home/robbie/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

sudo net usershare info = nothing

robbie@robbie-laptop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
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

smbtree
WORKGROUP
	\\ROBBIE-LAPTOP  		robbie-laptop server (Samba, Ubuntu)
		\\ROBBIE-LAPTOP\documents      	
		\\ROBBIE-LAPTOP\IPC$           	IPC Service (robbie-laptop server (Samba, Ubuntu))
		\\ROBBIE-LAPTOP\print$         	Printer Drivers
CA

robbie@robbie-laptop:~$ find smb
find: `smb': No such file or directory
robbie@robbie-laptop:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.122   ROBBIE-LAPTOP +[WORKGROUP] [Unix] [Samba 3.4.0]

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-01-06 13:57 EST
Interesting ports on 192.168.1.122:
Not shown: 998 closed ports
PORT    STATE SERVICE
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap done: 1 IP address (1 host up) scanned in 11.74 seconds

---

### Post by Morbius1 on 2010-01-06
Well, your share definition and smb.conf file seems to be OK. The problem is with smbtree and nmap. There's only one machine on your network and that's ROBBIE-LAPTOP.

The first thing I would do is disable any firewalls you have on any of the machines. If you've done a standard install and haven't changed the firewall I'd leave it alone.

Is 192.168.1.122 ROBBIE-LAPTOP ?

---

### Post by bobbyhenery on 2010-01-06
Is 192.168.1.122 ROBBIE-LAPTOP ? ==> [COLOR=RoyalBlue]YES[/COLOR]

Your help is very much appreciated!

---

### Post by Morbius1 on 2010-01-06
I take it disabling any firewall did nothing?

What's odd about nmap is that it doesn't even display the router's ip address. Can you ping any of the the other machines on the network. ?

By ping I mean in a terminal type: **ping 192.168.0.100** where 192.168.0.100 is the ip address of another box on the network.

---

### Post by Morbius1 on 2010-01-06
hakan8470,

You do not have the same problem since your error message isn't listed in the original posters output. Please start your own thread.

This forum is chaotic enough without these side trips ;)

---

