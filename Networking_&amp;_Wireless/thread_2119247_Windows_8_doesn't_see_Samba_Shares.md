---
title: "Windows 8 doesn't see Samba Shares"
date: 2013-02-23
forum: Networking &amp; Wireless
---

### Post by bmather9 on 2013-02-23
So I've been running an ubuntu server for about 6 months now (noob) and I set up a samba share which I used with windows 7 PC's.  Once it was set up everything worked fine.  

Now I have 2 windows 8 PC's and neither of them have my ubuntu server samba share showing up with network discovery.  If I use the IP or hostname (\\ubunutu) the shares show up and work properly. 

I just double checked and my windows 7 machine still automatically discovers the server, but neither windows 8 machine does.  What could be my problem?

smb.conf
> [global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	domain master = yes
	username map = /etc/samba/user.map
	map to guest = bad user
	encrypt passwords = yes
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	wins support = true
	dns proxy = no
	netbios name = Ubuntu Server
	server string = %h server (Samba, Ubuntu)
	unix password sync = yes
	local master = yes
	workgroup = WORKGROUP
	os level = 65
	syslog = 0
	preferred master = yes
	panic action = /usr/share/samba/panic-action %d
	usershare allow guests = yes
	max log size = 1000
	pam password change = yes

---

### Post by bab1 on 2013-02-23
> **bmather9 said:**
> So I've been running an ubuntu server for about 6 months now (noob) and I set up a samba share which I used with windows 7 PC's.  Once it was set up everything worked fine.  

Now I have 2 windows 8 PC's and neither of them have my ubuntu server samba share showing up with network discovery.  If I use the IP or hostname (\\ubunutu) the shares show up and work properly. 

I just double checked and my windows 7 machine still automatically discovers the server, but neither windows 8 machine does.  What could be my problem?

smb.conf
The fact that you can directly connect to the share tells me that the Samba server (smbd) is working.  Also, the fact that you can't browse the network tells me that the Samba naming daemon (nmbd) is not working properly.

You mention that the server name is \\ubuntu but you have explicitly used the following in your smb.conf file ```
netbios name = Ubuntu Server
```...this is wrong.  The netbios name should be not have any spaces in it (and be less than 15 characters).  If you explicitly declare the netbios name, the nmbd daemon will not look at the hostname to convert to the netbios name.  What is the hostname of this machine?

In addition you have made this server the WINS server for the network```
wins support = true
```... I'll bet you  haven't configured the clients to use it.  For a single segment LAN (1 subnet) you don't need a WINS server.  As a matter of fact the documentation discourages the use.  The default is ```
[COLOR="Blue"]wins support = no [/COLOR]
```...Do you have a multi subnet network?

I would start by returning all the [global] parameters to their defaults and see if that helps, but since I have no direct Widows 8 experience it's an experienced guess.

---

### Post by bmather9 on 2013-02-23
Good news!  The combination of your 2 suggestions fixed my problem; I'm not sure which was the culprit, but it seems to be working well now.  The hostname of my machine is UBUNTU and I set the netbios name to be the same thing.  

I find it strange that windows 7 didn't seem to have a problem using "Ubuntu Server" as the netbios name but window 8 does.  

To answer your questions I do not have a multi subnet network. 

Thanks for your help!

---

