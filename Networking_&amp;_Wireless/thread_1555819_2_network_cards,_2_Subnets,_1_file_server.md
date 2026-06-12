---
title: "2 network cards, 2 Subnets, 1 file server"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by burnleyhome on 2010-08-18
I'm new to Linux, using Ubuntu 10.04 as a file server and DHCP.
I have 2 networks,
1 = office 192.168.0.x = DHCP server to clients
2 = industrial 192.168.20.x = all have static IPs

My old Win2000 box had 2 network cards with 192.168.0.6 and 192.168.20.19 and I used this to file share on both networks. I changed to Ubuntu 10.04 and would like to do the same.

I have the office network fully working with Ubuntu working as DCHP server and I'm using Samba as a file server (bit of learning for correcly setting up permissions with UCL but its now great).

I connected the industrial network to eth1 (192.168.20.19) and I can ping all the computers from Ubuntu and I can ping Ubuntu from the PC's (all running Win Xp Pro). What I cannot do is connect to Ubuntu with Windows Explorer as in I cannot see the server (using windows find computers or typing the IP in address bar or net view). If I connect the industrical network into my office network, I can now see the server.

My ifconfig
eth0      Link encap:Ethernet  HWaddr 84:2b:2b:15:e2:fc  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::862b:2bff:fe15:e2fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14562638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8137538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20149635734 (20.1 GB)  TX bytes:991929727 (991.9 MB)
          Interrupt:16 Memory:da000000-da012800 

eth1      Link encap:Ethernet  HWaddr 84:2b:2b:15:e2:fd  
          inet addr:192.168.20.19  Bcast:192.168.20.255  Mask:255.255.255.0
          inet6 addr: fe80::862b:2bff:fe15:e2fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68858 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13834160 (13.8 MB)  TX bytes:35488041 (35.4 MB)
          Interrupt:17 Memory:dc000000-dc012800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42938 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42938 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5096601 (5.0 MB)  TX bytes:5096601 (5.0 MB)


My smb.conf
[global]
	server string = SRVEX
	workgroup = creativeus
	security = user
	hosts allow = 127. 192.168.0.0/24 192.168.20.0/24
	interfaces = 127.0.0.1/8 eth0 eth1
#	hosts allow = 127. 192.168.0. 192.168.20.
#	interfaces = 127.0.0.1/8 192.168.0.0/24 192.168.20.0/24
	bind interfaces only = yes
	remote announce = 192.168.0.255 192.168.20.255
	remote browse sync = 192.168.0.255 192.168.20.255

#added to avoid getting chdir ???? failed errors
	client lanman auth = yes

#added to avoid "getpeername failed. Error was Transport endpoint is not connected" errors in syslog
;	smb ports = 139

#added to stop CUPS print errors in syslog
	load printers = no 
	show add printer wizard = no
;	printing = none
	printcap name = /dev/null
	disable spoolss = yes

;	printcap name = cups
;	enable spoolss = no
	cups options = raw
	log file = /var/log/samba/samba.log
	max log size = 1000
	username level = 6
	password level = 6
	unix password sync = yes
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	local master = no
	domain master = no
	os level = 33
	logon drive = m:
	logon home = \\%L\homes\%u
	logon path = \\%L\profiles\%u
	logon script = %G.bat
	name resolve order = wins lmhosts bcast
	wins support = yes
	dns proxy = no
	client use spnego = no
	client signing = no
	client schannel = no
	server schannel = no
	allow trusted domains = no
	obey pam restrictions = yes
	follow symlinks = no
	update encrypted = yes
	passwd chat timeout = 120
	username map = /etc/samba/smbusers
	passwd program = /usr/bin/passwd '%u'
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	add group script = /usr/sbin/groupadd '%g'
	delete user script = /usr/sbin/userdel '%u'
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	delete group script = /usr/sbin/groupdel '%g'
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	machine password timeout = 120
	idmap uid = 16777216-33554431
	idmap gid = 16777216-33554431
	template shell = /dev/null
	winbind use default domain = yes
	winbind separator = @
	winbind cache time = 360
	winbind trusted domains only = yes
	winbind nested groups = no
	winbind nss info = no

[homes]
	comment = Home Directories
	path = /home/%u/Documents
	valid users = %S
	writeable = yes

[public]
	path = /home/shared/public
	writeable = yes
	guest ok = yes

+ other shared drives

---

### Post by endotherm on 2010-08-18
I;m noticing that this line is malformed:
```
hosts allow = 127. 192.168.0.0/24 192.168.20.0/24
```

try running 'testparm' to see if there are any other errors in your config file.

---

### Post by burnleyhome on 2010-08-18
No errors. Only a warning that my share names are over 12 characters long.

How should that line read?
I used tutorials to create all my files and forums to modify them when problems occurred. I think I'm at the stage where I know enough to be dangerous.

---

### Post by endotherm on 2010-08-18
just drop the '127.' token. IP addresses aren't usually referred to in part.
I would change it to 
```
hosts allow = 192.168.0.0/24 192.168.20.0/24
```
also you have one of the longest smb.conf global sections I have ever seen. I would start commenting out the more esoteric options, like the winbind settings. 

I also see that you are specifying "lanman" client authentication. 
lanman is long dead and most modern windows clients will not use it unless specifically configured to do so. 
try adding:
```
client NTLMv2 auth = yes
```lastly are you getting a problem reaching the server or logging in? do you recieve a error message of some kind?

---

### Post by burnleyhome on 2010-08-18
Nice one mate that fixed it.

I did the changes you recommended and I can now connect to the server. Previously I could ping the server (192.168.20.19), but when trying to connect to it, it would just come back without connecting.

Thanks so much

Chris

---

