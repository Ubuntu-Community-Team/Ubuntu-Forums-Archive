---
title: "IP addressing and DNS help. Setting up connection to existing Network"
date: 2011-09-23
forum: Networking &amp; Wireless
---

### Post by PayPaul on 2011-09-23
I am trying to setup file sharing and access to my existing home network. I get the message that packages haven't been installed for this to work. I was told by some here that DNS needs to be setup. I've attempted that by editing the Etho0 settings with almost disastrous results. I'm a complete noob to Ubuntu network setups. Can someone walk me through the DNS or better yet point to the packages that need to be installed in order for network access to work. I can access the Internet through the Belkin 4g router but can't see other machines on the network nor, of course, those machine see mine.

---

### Post by capscrew on 2011-09-23
> **PayPaul said:**
> I am trying to setup file sharing and access to my existing home network. I get the message that packages haven't been installed for this to work. I was told by some here that DNS needs to be setup. I've attempted that by editing the Etho0 settings with almost disastrous results. I'm a complete noob to Ubuntu network setups. Can someone walk me through the DNS or better yet point to the packages that need to be installed in order for network access to work. I can access the Internet through the Belkin 4g router but can't see other machines on the network nor, of course, those machine see mine.

What packages does the message say are missing?

If you are going to use Network Manager for this interfaces you should not directly edit the eth0 settings directly.  How do you want to setup the IP addressing: DHCP or Static -- manually editing the conf files or via Network Manager?

---

### Post by PayPaul on 2011-09-23
> **capscrew said:**
> What packages does the message say are missing?

If you are going to use Network Manager for this interfaces you should not directly edit the eth0 settings directly.  How do you want to setup the IP addressing: DHCP or Static -- manually editing the conf files or via Network Manager?

The "packages" are not specified. It looked a lot like, sheesh, a Windoze error dialog. 

I think normally, or shall I say, under Windoze, it was a DHCP setup using their network wizard. Of course under Ubuntu it's a little more direct and detailed. I hope I even have network Manager installed. If I do will setting up the network machines and IP addressing to DHCP solve my network access issue?

---

### Post by capscrew on 2011-09-23
> **PayPaul said:**
> The "packages" are not specified. It looked a lot like, sheesh, a Windoze error dialog. 

I think normally, or shall I say, under Windoze, it was a DHCP setup using their network wizard. Of course under Ubuntu it's a little more direct and detailed. I hope I even have network Manager installed. If I do will setting up the network machines and IP addressing to DHCP solve my network access issue?

This is not a Windows machine.  You will be better off if you don't try and relate what you see to a windows host.  Does this host have Internet connectivity now?  Can you connect to sites on the Internet?

What version of Ubuntu did you install?

Post the output of these commands from the terminal```
ifconfig -a

cat /etc/network/interfaces


```

---

### Post by PayPaul on 2011-09-23
> **capscrew said:**
> This is not a Windows machine.  You will be better off if you don't try and relate what you see to a windows host.  Does this host have Internet connectivity now?  Can you connect to sites on the Internet?

What version of Ubuntu did you install?

Post the output of these commands from the terminal```
ifconfig -a

cat /etc/network/interfaces


```

I'm going to post this code results but wish that I know how to post it so it scrolls down.

if config -a

```
paulw@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

paulw@ubuntu:~$ gedit /etc/resolv.conf
paulw@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:21:b5:2b:e5  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::224:21ff:feb5:2be5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:350069 errors:0 dropped:0 overruns:0 frame:0
          TX packets:225931 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:438289499 (438.2 MB)  TX bytes:32888112 (32.8 MB)
          Interrupt:44 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49888 (49.8 KB)  TX bytes:49888 (49.8 KB)
```

For the 2nd one:

paulw@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

I hope I got that right and it makes sense to you or anyone else reading this...

---

### Post by capscrew on 2011-09-23
> **PayPaul said:**
> I'm going to post this code results but wish that I know how to post it so it scrolls down.

if config -a

```
paulw@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

paulw@ubuntu:~$ gedit /etc/resolv.conf
paulw@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:21:b5:2b:e5  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::224:21ff:feb5:2be5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:350069 errors:0 dropped:0 overruns:0 frame:0
          TX packets:225931 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:438289499 (438.2 MB)  TX bytes:32888112 (32.8 MB)
          Interrupt:44 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49888 (49.8 KB)  TX bytes:49888 (49.8 KB)
```

For the 2nd one:

paulw@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

I hope I got that right and it makes sense to you or anyone else reading this...

It means that you have a wired interface managed by Network Manager.  Most likely it is a DHCP assigned IP address.  Can you confirm this by looking at Network Manager's GUI interface.  Sorry I can't tell you how to do that, but it should be simple.  I don't use/need Network Manager for any of my machines.

What about this part> [COLOR="Blue"]Does this host have Internet connectivity now?  Can you connect to sites on the Internet?

What version of Ubuntu did you install?[/COLOR]

---

### Post by PayPaul on 2011-09-23
"[COLOR=Blue]Does this host have Internet connectivity now?  Can you connect to sites on the Internet?

What version of Ubuntu did you install?"

[COLOR=Black]It does, of course, have Internet connectivity

Ubuntu 11.04.[/COLOR]


[COLOR=Black]I just tried to do a shared folder and finally got a prompt to install a Windows network sharing package. It also prompted me to log out and log back in. I still can't see the network. I also tried to disallow or not require IpV4 but to no avail. I am using network manager. Though Ubuntu calls it "Network Connections". [/COLOR]
[/COLOR]

---

### Post by capscrew on 2011-09-23
> **PayPaul said:**
> "[COLOR=Blue]Does this host have Internet connectivity now?  Can you connect to sites on the Internet?

What version of Ubuntu did you install?"

[COLOR=Black]It does, of course, have Internet connectivity

Ubuntu 11.04.[/COLOR]


[COLOR=Black]I just tried to do a shared folder and finally got a prompt to install a Windows network sharing package. It also prompted me to log out and log back in. I still can't see the network.
That's normal for starting out.  Do you have a folder shared by right clicking and ticking all the boxes?> 

I also tried to disallow or not require IpV4 but to no avail. 
Why would you do that?  You need IPv4 networking to share the folders and to connect to the Internet.> 
I am using network manager. Though Ubuntu calls it "Network Connections". [/COLOR]
[/COLOR]
It is the same thing.  Network Manager is the app that manages the connections.

If you have shared a folder you should have a /etc/samba/smb.conf file.  Lets see what is in it.  Post the output of ```
testparm -s
```

---

### Post by PayPaul on 2011-09-23
> **capscrew said:**
> That's normal for starting out.  Do you have a folder shared by right clicking and ticking all the boxes?Why would you do that?  You need IPv4 networking to share the folders and to connect to the Internet.
It is the same thing.  Network Manager is the app that manages the connections.

What happened instead was a new wired connection was created. Not an Ethos but something called "wired connection 1". It had no MAC address or much of anything else. The original Ethos1 wasn't modified at all it seems.

[/QUOTE]If you have shared a folder you should have a /etc/samba/smb.conf file.  Lets see what is in it.  Post the output of ```
testparm -s
```[/QUOTE]

Here are the results of your suggested command parameter:

paulw@ubuntu:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
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

---

### Post by PayPaul on 2011-09-23
I was also able to ping one of the IP addresses on my network. I received and transmitted packets to it. But now I need to know how to actually find the computers on this network. I don't see them list when I go into the the Ubuntu equivalent of Explorer. I'm not sure what that's called.

I've been able to see one of the computers on the Network, a Vista machine. I went to "go" in the file manager, clicked on network and found the Windows Workgroup that it belongs to. However, the other machine in that workgroup, an XP machine, I can not see nor access.

---

### Post by capscrew on 2011-09-23
> **PayPaul said:**
> I was also able to ping one of the IP addresses on my network. I received and transmitted packets to it. But now I need to know how to actually find the computers on this network. I don't see them list when I go into the the Ubuntu equivalent of Explorer. I'm not sure what that's called.

Slow down -- all will be revealed.  :-)

---

### Post by capscrew on 2011-09-23
> **PayPaul said:**
> What happened instead was a new wired connection was created. Not an Ethos but something called "wired connection 1". It had no MAC address or much of anything else. The original Ethos1 wasn't modified at all it seems.

The label *eth0 * is also just a label for the interface.  Not sure where you looked for the information, but it is not relevant at this moment for what you want to do.> 

If you have shared a folder you should have a /etc/samba/smb.conf file.  Lets see what is in it.  Post the output of ```
testparm -s
```> 

Here are the results of your suggested command parameter:

```
paulw@ubuntu:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
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

My suggestion is to use NetBIOS with your existing DHCP setup.  It's the simplest to set up.  All you need to do is edit the /etc/samba/smb.conf file.  Use the file above as an example.  The changes will be in red (see above).

First you need to provide a NetBIOS name for your machine (less than 15 charaacters)  See the [global] section in the above file.

---

### Post by PayPaul on 2011-09-23
I can see a Workgroup that is the name of the Windows network which I thought I had also set this computer and the Ubuntu installation to be part of in the beginning. However when I click on the only computer on that network that I can see there is a prompt for a password. I'm also seeing the default name of "workgroup" listed. How do I ascertain the "workgroup" this machine is part of? In a windows network setup all that's needed is to choose a workgroup name which was the name of the network I established before the addition of this machine (running win7 at the time). Here in Ubuntu. I can't be too sure of where to find and modify that information. I would think that same logic would follow. If my Ubuntu install on this machine is also designated as choosing the workgroup name of my network, I would be able to access all the shared files on that named network.

---

### Post by capscrew on 2011-09-23
> **PayPaul said:**
> What happened instead was a new wired connection was created. Not an Ethos but something called "wired connection 1". It had no MAC address or much of anything else. The original Ethos1 wasn't modified at all it seems.

The label *eth0 * is also just a label for the interface.  Not sure where you looked for the information, but it is not relevant at this moment for what you want to do.> 

If you have shared a folder you should have a /etc/samba/smb.conf file.  Lets see what is in it.  Post the output of ```
testparm -s
```> 

Here are the results of your suggested command parameter:

```
paulw@ubuntu:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
        [B][COLOR="Red"]netbios name = payPaul
        name resolve order = bcast lmhosts host wins[/COLOR][/B]
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

My suggestion is to use NetBIOS with your existing DHCP setup.  It's the simplest to set up.  All you need to do is edit the /etc/samba/smb.conf file.  Use the file above as an example.  The changes will be in red (see above).

First you need to provide a NetBIOS name for your machine (less than 15 characters) and set the name resolve order so it uses broadcasts first.  See the [global] section in the above file (in red) for the exact wording.

The reboot the system.  When the system comes up I want you to check to make sure the Samba daemons are running.  In the terminal run the following command```
pgrep -l mnd
```

This will display the smbd and nmbd daemons and PID numbers.  It will look like this  ```
pgrep -l mbd
972 smbd
1027 nmbd
1111 smbd

```

---

### Post by capscrew on 2011-09-23
> **PayPaul said:**
> I can see a Workgroup that is the name of the Windows network which I thought I had also set this computer and the Ubuntu installation to be part of in the beginning. 
Windows workgroups are only for visual purposes.  To associate like shares (i.e all sales or pictures or sports).  They are not part of any network and you can have as many workgroups as you want.  We can deal with that later.> 

However when I click on the only computer on that network that I can see there is a prompt for a password. I'm also seeing the default name of "workgroup" listed. How do I ascertain the "workgroup" this machine is part of? 
By adding that information ( we can do that later).> 
In a windows network setup all that's needed is to choose a workgroup name which was the name of the network I established before the addition of this machine (running win7 at the time). 
Uh huh...> 
Here in Ubuntu. I can't be too sure of where to find and modify that information. I would think that same logic would follow. If my Ubuntu install on this machine is also designated as choosing the workgroup name of my network, I would be able to access all the shared files on that named network.
It 'aint necessarily so...

---

### Post by PayPaul on 2011-09-24
When I view the smb.conf file I don't even see what testparm -s command shows me. In fact it's a list of directions for the setup for the most part with some settings included. This particular passage of it intriqued me...


# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
    dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes

And this one...

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
    dns proxy = no

Why is it that this actual file in the place you indicate doesn't look anything like the entries in the command I entered in terminal? Not only that but the file itself is "read only". Hmmm. I'd have to change the permissions on it to do anything with it.

---

### Post by capscrew on 2011-09-24
> **PayPaul said:**
> When I view the smb.conf file I don't even see what testparm -s command shows me. In fact it's a list of directions for the setup for the most part with some settings included. This particular passage of it intriqued me...


# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
    dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes

And this one...

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
    dns proxy = no

Why is it that this actual file in the place you indicate doesn't look anything like the entries in the command I entered in terminal? Not only that but the file itself is "read only". Hmmm. I'd have to change the permissions on it to do anything with it.

The command *testparm * reads the file /etc/samba/smb.conf and displays only the parameters that are** not commented out**.  The lines that start with this symbol (#) are only comments.

None of the items that *"intrigued"  *you need to be changed in your setup.  The file can be edited if you use root privileges when using your editor.

To elevate your privileges when editing the file use sudo from the terminal (nano or vim editors) or gksudo for a GUI based editor like gedit.  You can can also use **Alt-f2 ** and type *gksudo gedit /etc/samba/smb.conf*.  What editor do you want to use?

Do not change any permissions at this time.

---

