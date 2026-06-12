---
title: "Unable to mount location: Failed to retrieve share list from server"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by texmorgan on 2009-02-27
I've never had a problem setting up Samba shares before but I just moved and got a new router, Netgear's WNR854T.  I originally thought this was an Apache based issue but I still get this error after turning Apache off completely.  Also, both computers can get to the internet with no problem.

My setup is as follows:
All systems are running Ubuntu 8.10
Laptop: 192.168.1.2
Desktop: 192.168.1.4

If I try to telnet to 127.0.0.1 on either it rejects the connection which shouldn't happen but is.

Do I need to set up the servers in the hosts file?  Is there some place I need to change the list of boxes that can access each other?

Normally, I'll get a prompt asking for login credentials before it tries to connect to the Samba share but I'm not even getting to that point.  I try to connect to the computer and then this error is thrown.

Please help!!! I don't want to have to go buy a USB drive just so I can transfer files between two perfectly good computers that are next to each other.

---

### Post by dannyboy79 on 2009-02-27
> **texmorgan said:**
> I've never had a problem setting up Samba shares before but I just moved and got a new router, Netgear's WNR854T.  I originally thought this was an Apache based issue but I still get this error after turning Apache off completely.  Also, both computers can get to the internet with no problem.

My setup is as follows:
All systems are running Ubuntu 8.10
Laptop: 192.168.1.2
Desktop: 192.168.1.4

If I try to telnet to 127.0.0.1 on either it rejects the connection which shouldn't happen but is.

Do I need to set up the servers in the hosts file?  Is there some place I need to change the list of boxes that can access each other?

Normally, I'll get a prompt asking for login credentials before it tries to connect to the Samba share but I'm not even getting to that point.  I try to connect to the computer and then this error is thrown.

Please help!!! I don't want to have to go buy a USB drive just so I can transfer files between two perfectly good computers that are next to each other.
post output of command please:
```
findsmb
```

```
sudo iptables -L
```

you can try these from both computers. Also, are you using a WINS Server or counting on a hosts file to connect hostnames to ip addresses?

---

### Post by texmorgan on 2009-02-27
Both show the same as below...

> **dannyboy79 said:**
> post output of command please:
```
findsmb
```

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.4     ROMULUS        [WORKGROUP] [Unix] [Samba 3.2.3]
192.168.1.102   WASP          +[WORKGROUP] [Unix] [Samba 3.2.3]


```
sudo iptables -L
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


you can try these from both computers. Also, are you using a WINS Server or counting on a hosts file to connect hostnames to ip addresses?


I'm not using a WINS Server or relying off a host file to connect the hostnames to IPs.

---

### Post by dannyboy79 on 2009-02-27
now try this:
```
smbclient -L ROMULUS
```
from the WASP computer.

and 

```
smbclient -L WASP
```
from the ROMULUS computer.

if it asks you for a password, don't enter anything, just hit enter, this is anonymous samba login. if that returns nothing than you have no shares defined for anonymous access. if when it does ask for a password, and you enter the password for that machine, it should show you a list of shares if any are available. good luck

---

### Post by pcjunkie on 2009-03-04
This is what I am getting intermittently

gamer@gamer-desktop:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
gamer@gamer-desktop:~$ sudo iptables -L

 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
gamer@gamer-desktop:~$ smbclient -L ROMULUS
Connection to ROMULUS failed (Error NT_STATUS_BAD_NETWORK_NAME)
gamer@gamer-desktop:~$ smbclient -L WASP
Connection to WASP failed (Error NT_STATUS_BAD_NETWORK_NAME)
gamer@gamer-desktop:~$

---

### Post by dannyboy79 on 2009-03-04
i am still on Feisty so this may be in a different place but do you have the same 
workgroup = foo
defined in your /etc/samba/smb.conf for both machines? Also, can you paste your smb.conf files from each machine on [www.pastebin.com](www.pastebin.com) and then paste those links back here so I can compare the 2. thanks.

---

### Post by pcjunkie on 2009-03-05
```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = WORKGROUP

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



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
	log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
	max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
	syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
	panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
	encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
	passdb backend = tdbsam

	obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
	unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
	pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
	map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;	printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes
	username map = /etc/samba/smbusers

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
	comment = All Printers
	browseable = no
	path = /var/spool/samba
	printable = yes
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[Desktop]
	path = /root/Desktop
	writeable = yes
;	browseable = yes
	valid users = gamer

[media]
	path = /media
	writeable = yes
	browseable = no
	valid users = gamer
```

Reinstalled everything..

Upgraded from 7.10 to 8.10 still the same..
Windows can't log in using the Ubuntu account / password
Ubuntu fails to see WIndows 

After initially installing with basic networking the shares worked but after 2 hours they dropped out and would refuse connections / passwords.

---

### Post by macromike on 2009-03-18
I'm not sure if this will help, but I was having the same problem and it turned out that the firewall in ubuntu was blocking the netbios ports (TCP port 139) needed to make name resolution work properly when browsing the windows network.

I solved it by installing & running gufw (gui for uncomplicated firewall) and going to the Preconfigured tab to tell it to allow the netbios-ssn service and the nfs service.

---

### Post by timoftheecat on 2009-04-03
I did all of these things with successful instalation to applying the changes to no avail....still recieving the "Unable to mount location: Failed to retrieve share list from server" error message

---

### Post by WrathofthePenguin on 2009-04-03
I was working with somebody else on this same kind of problem. The packet captures he gave me showed that his router was not returning an IP address for the name. It was learned through nbns. Now in general I don't think that should make a big difference, but I noticed that there was an error being returned that the device was not listening for called name.

I had him make host file entries and now it is working.

---

### Post by rodercot on 2009-04-07
Just too add to the confusion, I use mythbuntu 8.10 with xfce and pyNeighborhood and I get the same errors in py as well BUT if from terminal I issue a 

 smbclient -L //ipaddressofserver -u% It will easily lists all the shares on that media server which are 12 drives but I still cannot browse them from pyNeighborhood.

 This is very frustrating I have been trying to set up mythvideo on my Master Back End since Saturday Morning at 5AM. 

 Dave

---

### Post by taiji_jian on 2009-04-11
There is a serious difficulty here in that the error message is ridiculously vague. I've been having this problem for a couple of days for no reason that I can figure out. Doing web searches for the error message takes me to bug reports that are CLEARLY not my problem (hostname collision). 

My particular version of this issue seems to have something to do with DNS. Smbtree gives me a lot of "timeout connecting to 208.69.36.132:445" and 
"208.69.36.132:139" errors. Why samba would suddenly start trying to use OpenDNS to resolve NetBIOS names is a mystery to me.

---

### Post by Jimmy9pints on 2009-04-12
I get the same error. Always have everytime I tried to set up a samba server/client. 

And the same as taiji_jian I get the "timeout connecting to 208.69.36.132:445" when trying to connect from the command line.

---

### Post by Snicket on 2009-04-13
> **macromike said:**
> I'm not sure if this will help, but I was having the same problem and it turned out that the firewall in ubuntu was blocking the netbios ports (TCP port 139) needed to make name resolution work properly when browsing the windows network.

I solved it by installing & running gufw (gui for uncomplicated firewall) and going to the Preconfigured tab to tell it to allow the netbios-ssn service and the nfs service.

I don't know how, but this fix helped solve my issue of Vista not seeing Ubuntu. Weird :S.

However, I still can't access my Vista desktop for printer or file sharing.
I would greatly appreciate any help.

---

### Post by sbyte on 2009-04-22
I get this happening to me a fair amount of time, however when it happens only the windows computers can talk to each other. when i do a "findsmb"
i can see:
my house mates XP laptop,
my 8.10 laptop,
and my 8.10 desktop (from which i am running the commands),
i cannot view my house mates XP Desktop.

if i open up the network in nautilus, i get the aforementioned "unable to mount location...."

my workaround is to open up FireFox, and enter "smb://192.168.0.199/", the location of my house mates XP laptop, which allows me to see the shares. 

once i can see the shares in FF, nautilus will allow me to browse them.

might work for you too :-)

---

### Post by dreperk on 2009-04-22
> **Snicket said:**
> I don't know how, but this fix helped solve my issue of Vista not seeing Ubuntu. Weird :S.

However, I still can't access my Vista desktop for printer or file sharing.
I would greatly appreciate any help.

In Vista go to the Network & Sharing Center (either under Control Panel or right-click the network connection icon in system tray).  I can't remember off hand what the exact terminology is, but there you can turn off "Password Protected Sharing".  This seems to solve a lot of Vista sharing issues.  Also, it goes without saying, make sure file sharing is turned on as well.

---

### Post by Snicket on 2009-04-22
> **dreperk said:**
> In Vista go to the Network & Sharing Center (either under Control Panel or right-click the network connection icon in system tray).  I can't remember off hand what the exact terminology is, but there you can turn off "Password Protected Sharing".  This seems to solve a lot of Vista sharing issues.  Also, it goes without saying, make sure file sharing is turned on as well.

I already had those options set. Still, it doesn't budge :/.

---

### Post by conorturton on 2009-04-23
THIS IS A CONTINUATION OF THE WINDOWS PASSWORD PROTECTED NETWORK SHARE BUG that has been going on since 8.04 was released.

Basically, when Gnome changed to ver 2.24 and started using gvfs-smb, someone cocked up the authentication routine so it doesn't ask for any and the remote machine times out the connection request.

Currently nobody knows how to fix it and whatever fixes have been implemented seem to have just changed the type of error it throws up rather than solving the problem.

You'll find that in every other desktop than Gnome, it all works fine which is why it also lists the shares in terminal. You'll find that if you know the IP address and the share name and select "Connect to Server", Gnome will ask for a password.

It's broken but the sad fact is that the Gnome team don't seem interested in fixing it because its to do with connecting to Windows so they don't care.

---

### Post by game_plan on 2009-04-26
I'll agree that the problem started in 8.04 but don't think the problem is Gnome alone since my machines running other distributions are working.

My problem is the same only with Samba file shares. A while ago Fedora was doing the same thing but tweaking SeLinux & IPtables fix it.

How do you edit SeLinux rules in Ubuntu?

---

### Post by XopherH on 2009-04-28
I am getting this error now after upgrading from 8.10 to 9.04

everything was working flawlessly until Samba was reinstalled an hour ago during the upgrade.  that is the only change that was made.

---

### Post by VictorR on 2009-04-30
I can confirm, that this bug did not appear, while I was testing Ubuntu 9.04 from live-CD. After I **upgraded** my 8.10 to 9.04, I still suffer from this nasty bug. I can get through the network to see connected computers, but to reach any shared folder from my Ubuntu machine I have to type something like
smb://192.168.0.2/share_name
into Nautilus address field.
To check this behaviour, I run live-CD on another computer and could easily connect to any Windows share. I also tested it with Ubuntu Netbook Remix loaded from USB-stick and had no problems.

So seems it is something wrong in configuration files, which are not updated during upgrade process (I accepted replacing my old smb.conf with new one, but it did not help).

---

### Post by craig.o on 2009-05-02
Same symptoms here.

> Unable to mount location
Failed to retrieve share list from server

Client: Ubuntu 9.04 (fresh install)
Server: Debian 4.0 & Samba 3.024

---

### Post by lordmetroid on 2009-05-03
Might this not be a general problem with the protocol itself, I have noticed this happening on the machines in my home that has a version of Windows installed as well as the machines that have Linux installed.

In windows I use the Advance IP scanner by radmin [http://www.radmin.com/products/utilities/index.php](http://www.radmin.com/products/utilities/index.php) and that one do find the missing machines.
In Linux however I have no idea how to find them. However, when a new machine connects to the file sharing network the layout of the network seem update itself and I can yet again access all machines, it only happens sometimes though, as seemingly arbitrary whether or not the network layout will update.

---

### Post by fester225 on 2009-05-03
I just got rid of this error by doing a cold (unplugged) reboot on the router.

---

### Post by nsew on 2009-05-05
Hi all, 

Same goes here, 9.04, fresh install, can't browse network, other machine is running Vista Ultimate. 

I will relate some of my experience and what has been an acceptable workaround for me. Even though I am still not able to browse the network, and I still get the mount error, I am able to connect to the shares on the Vista machine using the "Connect to Server...".

Here were my steps, in order (to the best of my memory). Although I don't know if I could have used "Connect to Server", or used Nautilus to browse the shares before doing these things, or if it will work for anyone else.

> **dreperk said:**
> In Vista go to the Network & Sharing Center (either under Control Panel or right-click the network connection icon in system tray).  I can't remember off hand what the exact terminology is, but there you can turn off "Password Protected Sharing".  This seems to solve a lot of Vista sharing issues.  Also, it goes without saying, make sure file sharing is turned on as well.

Then

> **macromike said:**
> I'm not sure if this will help, but I was having the same problem and it turned out that the firewall in ubuntu was blocking the netbios ports (TCP port 139) needed to make name resolution work properly when browsing the windows network.

I solved it by installing & running gufw (gui for uncomplicated firewall) and going to the Preconfigured tab to tell it to allow the netbios-ssn service and the nfs service.

After I turned off Vista Password Protected Sharing I was able to use Firefox to browse: smb://192.168.0.104, but I stopped here and didn't try to see if I could see anything in Nautilus. I don't know why I didn't try Nautilus, but it's possible I could have been able to connect to the shares from this point.

> **sbyte said:**
> 
if i open up the network in nautilus, i get the aforementioned "unable to mount location...."

my workaround is to open up FireFox, and enter "smb://192.168.0.199/", the location of my house mates XP laptop, which allows me to see the shares. 

once i can see the shares in FF, nautilus will allow me to browse them.

might work for you too :-)


I then used smbclient to view/connect to the shared folders. 

```
universe@universe-laptop:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------

```
This didn't seem to show me anything.

But using -
```
smbclient -L //192.168.0.104
Enter universe's password: 
Domain=[ASUS] OS=[Windows Vista (TM) Ultimate 6001 Service Pack 1] Server=[Windows Vista (TM) Ultimate 6.0]

	Sharename       Type      Comment
	---------       ----      -------
	ADMIN$          Disk      Remote Admin
	C$              Disk      Default share
	D$              Disk      Default share
	IPC$            IPC       Remote IPC
	Public          Disk      
	Shared          Disk      
	Users           Disk      
session request to 192.168.0.104 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available

```
Showed the shares.

I noticed the NetBIOS over TCP disabled message, and still haven't looked into getting this sorted out yet. 

I tried to connect to the shares, and this worked.
```
universe@universe-laptop:~$ smbclient //192.168.0.104/Public/ asus
Domain=[ASUS] OS=[Windows Vista (TM) Ultimate 6001 Service Pack 1] Server=[Windows Vista (TM) Ultimate 6.0]
smb: \> ls
  .                                  DR        0  Thu Apr 30 18:15:27 2009
  ..                                 DR        0  Thu Apr 30 18:15:27 2009
  CyberLink                           D        0  Mon Nov  3 17:18:51 2008
  desktop.ini                       AHS      174  Mon Jan 21 13:41:56 2008
  Documents                          DR        0  Wed Dec 31 01:05:35 2008
  Downloads                          DR        0  Wed Oct 22 17:59:48 2008
  Favorites                         DHR        0  Mon Oct 20 19:31:13 2008
  Music                              DR        0  Fri Feb 27 02:44:44 2009
  Pictures                           DR        0  Thu Nov  2 23:49:43 2006
  Videos                             DR        0  Wed Nov 19 14:53:37 2008

		38155 blocks of size 4194304. 3423 blocks available
smb: \> 
 
```

A bit more digging around, and I found another post [http://forums.linuxmint.com/viewtopic.php?f=157&t=24407]("http://forums.linuxmint.com/viewtopic.php?f=157&t=24407"), shrugged my shoulders, and installed smb4k. Though this didn't seem to change anything when trying to browse the network.

After, I noticed the Connect to Server option. So, going to Places -> Connect to Server -> Service type = Windows Share. Filled in the details, and now I have the folders mapped, and appearing under Places. 

Additionally, I can browse via Nautilus without using the shares, as mentioned in one of the quoted sections.

Again, I understand this isn't a proper fix, and I'm rather clueless, but I thought to share my experience nonetheless. 

Will

---

### Post by XopherH on 2009-05-05
> **nsew said:**
> I decided to try going to Places -> Connect to Server -> Service type = Windows Share. Filled in the details, and now I have the folders mapped, and appearing under Places. 


This works for me.  thanks for showing me something new about the Ubuntu networking options, although this doesn't really solve the issue, it is an acceptable workaround.

Windows Share, Server : LAN IP, Folder: shared folder on server, My server user name, and Domain: your samba workgroup.

smb4k still doesn't connect as well as Network, and this must be done after reboot. Also, rebooting the server does not allow immediate access to all mounted folders and you have to use the link under Places before the desktop icon will work.

---

### Post by maphilli14 on 2009-05-13
I've never really had much success with nautilis and smb browsing/choosing.

I usually get this error:

```
Failed to mount Windows share
```

I'd love to know what the real work around is... I'm using smb4k on Jaunty.

TIA,

Mike

---

### Post by ken_23434 on 2009-05-14
Same issue here.  

[CENTER][B]"Unable to mount location 
 Failed to retrieve share list from server"[/B]
[LEFT]
I have 3 computers running XP.  They all can browse to my Ubuntu 9.04 shares (samba).  When I click <Places> -- <Network> on my Ubuntu machine, I can see the XP machines, but it fails to mount and show their shares.  The XP machines all can view the shares on each other.  I do not have any security or permissions set up to control access to the XP shares either.

Previously, I have accessed these shares using the Knoppix LiveCD.  To me, it seems like a Ubuntu issue also.

I print via the network to one of the XP machines from my Ubuntu box.
[/LEFT]
[/CENTER]

---

### Post by QwUo173Hy on 2009-05-16
Thanks Dannyboy79, your post [http://ubuntuforums.org/showpost.php?p=6809727&postcount=4](http://ubuntuforums.org/showpost.php?p=6809727&postcount=4)

solved this problem for me on Jaunty.

---

### Post by Phossy on 2009-05-17
I seemed to have solved my very similar problem in a very simplistic way.

Background Problem:

Upgraded an EEE PC 701P to EEEBUNTU and since then had not been able to mount my Windows server/ network or more importantly attach to my printer on the Windows server.

When I looked in Network (under PLACES on the Linux machine), I saw Windows Network and when I clicked on it I saw Home Network (which is the workgroup what my 2 windows machines were on). Clicking on Home Network - nothing visible. If I went into the Printer set-up I noticed that my 'Home Network' was now just seen as 'Home'.  All else having failed , 2 days scouring forums and trying all sorts, I reset up my Windows Network with a Workgroup name of 'home', rebooted my Linux Machine and all was well!

Now I may be totally off my trolley or could it be that somewhere in the system, Ubuntu only reads the first 4 characters of the Windows Workgroup, or perhaps reads up until it sees a space...

By the way - Linux Newbie (perhaps ignorance is bliss sometimes)

---

### Post by iiska on 2009-05-25
Found [this post]("http://ubuntuforums.org/showthread.php?t=531649") from forum archives which proposed adding entries for hosts in Windows network to /etc/hosts. That fixed this issue for me in Jaunty.

---

### Post by rbp on 2009-05-26
Apparently there is (still) a bug in nautilus so you can't connect to a password protected remote server by name.

The workaround is to use the IP address. So instead of:
```
smb://REMOTE_SERVER
```
use:
```
smb://192.168.1.1
```

That was the only way I could get it working.

Richard

---

### Post by dmizer on 2009-05-26
To fix the name browsing issue, please see this post: [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by Nogias Cid on 2009-06-05
hello i recently changed from windows to ubuntu(which rocks). i get the same error, i have 3 pcs, one running ubuntu 9.04 and the other 2 running ubuntu 8.10, however pc1 cannot view the drives on pc2 and 3 but pc2 and 3 can view each other and pc1 smoothly. in pc1 under places> network it shows Windows Network, when clicked it gives the error msg. any suggestions would be grateful. thanks

---

### Post by DaleKonle on 2009-06-11
This is an easy fix that worked for me. Change the resolve order.
 
Paste this line 
" name resolve order = lmhosts wins bcast host "
into the smb.conf file under this section: 

# What naming service and in what order should we use to resolve host names
# to IP addresses
 ; name resolve order = lmhosts host wins bcast" .

Put this in the command line to edit the file.
sudo gedit /etc/samba/smb.conf
 
Save the file, log off and back on.

See:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/375593](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/375593)

---

### Post by Nogias Cid on 2009-06-13
Still the same error appears

---

### Post by jarwadi on 2009-07-13
I have the same problem, couldnot connect to our local network and finally I got the problem in the smb.conf file

now I can log on and acces network flawlessly

Thanks so many

---

### Post by zackspade on 2009-07-23
This is my first post so sry if it seems noob. 

    Im running v9.04 jaunty and windowsXP version 2002 w/ service pack 2 in VirtualBox OSE.
      Windows under ubuntu in VBox i mean.
im trying to connect to my shared Docs through my network and i get said error.

    Plz help and remember im noob to ubuntu so no crazy wacked out 100 step terminal processes pls (exagerating of course). although i can deal with small terminal commands as long as u explain.

---

### Post by dmizer on 2009-07-23
The "Failed to retrieve share list from server" error is almost always firewall related. Try installing GUFW (via Synaptic Package Manager) and disabling the firewall in System > Administration > Firewall configuration.

Also, check Windows to make sure that no anti-virus or firewall is interfering on that end either.

---

### Post by xAirrick on 2009-07-25
**This is how I fix it.**

When browsing "Windows Network" I was also getting "unable to mount location" "failed to retrieve share list from server" 

when I connected my work laptop to the network I was able to see both workgroups  ("krft"  &  "workgroup")  I could browse the "krft" workgroup, but still got the error when trying to browse "workgroup"

findsmb helped ID the problem;

[SIZE=1][FONT=Courier New]root@EricUbuntu:/home/eric# findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.0.4     MAC0016CBAE1AAB [    WORKGROUP     ]
192.168.0.11    USWBAM7VNWYH1 +[KRFT] [Windows 5.1] [Windows 2000 LAN Manager]
192.168.0.21    ERICUBUNTU     [ERICUBUNTU] [Unix] [Samba 3.3.2][/FONT] 

[SIZE=2]192.168.0.4 is a MacMini.  I keep it on all the time as it is my HTPC.  somehow(maybe someone can explain this) it was responsible for the "workgroup" workgroup.  

I did 2 things **on the MacMini** to solve my browsing problem on ubuntu;
   1) rebooted it (it has been running for a couple months)
   2) System Preferences -> Network -> Advanced -> Wins  i set the workgroup to "workgroup"[/SIZE] 
[/SIZE]

---

### Post by roystreet on 2009-07-28
Hello: I am using ubuntu 9.04, freshly installed.

    I had the same issue & then while I was reading this post someone mentioned printers.  I have a printer that is on the network & plugged right into the router.  I decided to add that printer, even though I could see nothing on the network. It found the printer right away & added it as my default printer.  Then "suddenly" out of nowhere :D now it can see my whole network.  I'm slightly puzzled about this & I will do further research, but for now it's working.8)

I thought this might help someone out there having this problem.

~roystreet

By the way, I'm running this on a brand new HP laptop

---

### Post by elustran on 2009-08-02
> **macromike said:**
> I solved it by installing & running gufw (gui for uncomplicated firewall) and going to the Preconfigured tab to tell it to allow the netbios-ssn service and the nfs service.
That didn't quite work for me.  It turns out it didn't open quite the right ports.  I just fixed this problem on my 8.10 machine by opening up samba's ports on the gufw firewall (installable from Add/Remove) using TCP ports 139 and 445 and UDP ports 137-139.  137, 138, and 445 weren't open before.  Also, I don't seem to have to open the nfs port for samba to work.

---

### Post by noho.mirare on 2009-08-15
I solved the problem adding this line in samba.conf.

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = StPere
   netbios name = [COLOR=Red]machine_name[/COLOR]

and you can find[COLOR=Red] machine_name[/COLOR] in the prompt line of termina as you see below

user@[COLOR=Red]machine_name[/COLOR]:/home$ 

I hope to help someone

---

### Post by shields on 2009-08-15
> **noho.mirare said:**
> I solved the problem adding this line in samba.conf.

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = StPere
   netbios name = [COLOR=Red]machine_name[/COLOR]

and you can find[COLOR=Red] machine_name[/COLOR] in the prompt line of termina as you see below

user@[COLOR=Red]machine_name[/COLOR]:/home$ 

I hope to help someone

Where would one find the file, samba.conf?

Thanks.

---

### Post by dmizer on 2009-08-15
> **shields said:**
> Where would one find the file, samba.conf?

Thanks.

/etc/samba/smb.conf

For future refrence, you can find files via places > search for files or in the command line with the command:
```
whereis filename
```
or
```
locate filename
```

---

### Post by k4kelly on 2009-08-15
I'm having the same problem. I went through this post about 3 hour ago and have only gained a little.  I have 2 amd_64 desktop one running Ubuntu 9.04 the other Mythbuntu 9.04 and a laptop runing Vista_64. What really irks me is that 2 days ago the laptop and one of the desktops was communicating just fine. My main desktop (DALLAS-PC) would not
show the files on either of the other computers. The icons for all 3 computer plus a window network icon appear in the computer>Network folder. I started working on it again today and at first nothing was working. Now the Vista laptop will connect to either computer but the 2 desktop I get the Failed to retreive share list from server. This is the output of
findsmb on DALLAS-PC
192.168.1.100   GLENDA-DESKTOP+[GLENDA-DESKTOP] [Unix] [Samba 3.3.2]
192.168.1.101   DALLAS-PC      [KELLYHOME] [Unix] [Samba 3.3.2]

And this is the output of  smbclient -L DALLAS-PC
    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    dallas          Disk      Home Directories
    Documents       Disk      
    Pictures        Disk      
Anonymous login successful
Domain=[KELLYHOME] OS=[Unix] Server=[Samba 3.3.2]

    Server               Comment
    ---------            -------
    DALLAS-PC            dallas-pc server (Samba, Ubuntu)
    GLENDA-DESKTOP       glenda-desktop server (Samba, Ubuntu)

    Workgroup            Master
    ---------            -------
    KELLYHOME            GLENDA-DESKTOP
dallas@dallas-pc:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 

And on my wife's computer.
192.168.1.100   GLENDA-DESKTOP+[KELLYHOME] [Unix] [Samba 3.3.2]
192.168.1.101   DALLAS-PC      [DALLAS-PC] [Unix] [Samba 3.3.2]

The output of smbclient  -L GLENDA-DESKTOP
         DESKJET-990C       PRINTER  HEWLETT PACKARD
         word                     Disk
         excel                     Disk
         mypictures             Disk
         music                     Disk
         public                     Disk
Anonymous login successful
Domain=[KELLYHOME] OS=[Unix] Server=[Samba 3.3.2]
     DALLAS-PC                 dallas-pc server (Samba, Ubuntu)
     DGK-LAPTOP               MyLaptop
     GLENDA-DESKTOP       glenda-desktop server (Samba, Ubuntu)
  
    Workgroup            Master
    ---------            -------
    KELLYHOME            GLENDA-DESKTOP

I sure could use some help with this.

---

### Post by dmizer on 2009-08-16
> **k4kelly said:**
> I'm having the same problem.

The "failed to retrieve share list from server" error is almost always related to an interfering firewall.

Check the output of:
```
sudo iptables -L
```
If the output looks more complicated than the following:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
```
Then your firewall is probably interfering.

If you do not have a firewall in place on either of your machines, then please take a look at the 6th link in my sig.

You could also try using NFS for your file shares instead of Samba (since both of your machines are Linux based. If you would like to give that a shot, please see the 4th link in my sig.

---

### Post by Khidr9 on 2009-08-19
I just wanted to add for anyone having this issue that I have a D-Link Dir-655 router, and this problem was solved for me by updating to the latest firmware from the factory default.  Wish I had a good answer for why that's the case, but I got the idea after seeing that someone's cold reboot of the router fixed the issue, and knowing that it didn't help for me.

---

### Post by oz6702 on 2009-08-29
Ok my friends, here is the deal.

I'm sorry but I'm not too Linux - savvy (I am not computer illiterate but I am VERY new to Linux...)

and most of what I've read in this thread hasn't really made any sense to me. So I am going to lay out my problem and hope someone can help before I go mad and just set fire to my frikkin computer.

I am running Ubuntu 9.04, and my room mate is running Windows Vista 32 bit. I am trying to connect my box to his, so I can share files with him. I have a nice little crossover cable and I've hooked them together with it. I got on the Vista box and turned off password protection and enabled pretty much everything across the board just in case. You could look at this computer funny and access its files remotely, I swear. I set up a shared folder on the desktop, let's call it "Awesome shared files of Awesomeness".

Now, on my Ubuntu box, I can't seem to find much in the way of sharing options, but I did set a file to be shared. Let's call it "Linuxy Goodness".

The Ubuntu box is called Anne, the Vista box, Brick. Now, I can see Brick from Anne, but I can't connect. It says "Unable to mount location, failed to retrieve share list from server". I googled that error message and found this very thread. From Brick, I cannot see Anne at all. I have monkeyed with all sorts of settings and programs and I'm really afraid I'm just gonna screw it up more. So.... halp 0.o

I just want to send some files from Anne to Brick, because I need to reformat Anne's HDD. After reformatting and re-installing Ubuntu, I need to transfer my data back from Brick to Anne. That's it. I've seriously considered burning 25 DVD's to get this done (I have about 100 GB of stuff I don't care to get rid of), that's how much of a headache this had been. Sorry guys, I'm a nub, I don't know Ubuntu very well at all. I've only been using it for about 2 weeks. I like it a lot though ^_^

So can somebody maybe explain in layman's terms what is wrong and how I can fix it? I don't care if it's the most jerry-rigged, shoddy, temporary workaround ever, I just want it done ASAP. I don't have access to an external HDD or anything, its just the two PC's and the crossover cable. What the #!$#%@#$!#@$ is going on?????

:confused::confused::confused::confused::confused:


edit: seriously, +2 Internets to the man/woman/superintelligent shade of the color blue who can get this working for me...

---

### Post by dmizer on 2009-08-29
> **oz6702 said:**
> So can somebody maybe explain in layman's terms what is wrong and how I can fix it?

You should be able to fix it by following the directions located in the 6th link in my sig.

---

### Post by oz6702 on 2009-08-29
Thank you sirrah!
I am off to bed, but I will try this fix tomorrow. If it works, then huzzah!

If it doesn't, then huzzah anyways for your attempted assistance. I don't agree with Yoda, I think try is almost as good as do. Try indicates desire to help, and it's the thought that counts, right?

---

### Post by i-net on 2009-09-28
I have to same problem, and been digging and digging for the answer, so I tried a new approach, since i have VMware.
 
Here is the strange thing I came across!!!!
 
I loaded Kubuntu 9.04 up and in Dolphin type in the IP address and i'm prompted for my windows server username and password..... i type them in and walla I'm in.

---

### Post by zedstrange on 2009-09-29
what i cant work out is why my windows Xp computers can connect easily to any of the shares on my Ubuntu computers no problems at all.

But i can never get Ubuntu computers to connect to Ubuntu computers, this seems crazy to me!

Ihave googled and googled and googled and all i can find is how to connect Windows to Ubuntu shares, pages like this are no help at all,
[https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)

it just says "Other people on the same network (LAN) as you should now be able to access the folder" Oh i wish it were that easy.

None of the tips makes sense to me - if my windows computers can connect then it is a client issue not a server one?

Now i will try Dmizers tips anyway, see what happens.

---

### Post by Kerashi on 2009-09-30
I'm kind of new to linux (only been running Ubuntu about a week) and use it primarily as a home server to back up my Windows systems and to serve media to my ps3.  I believe I have overcome this error.  Here's how I did it.  

First, I stopped Samba with sudo /etc/init.d/samba stop  

Next, I edited smb.conf with sudo gedit /etc/samba/smb.conf  

In this file, I simply changed the workgroup name and saved.  

I then restarted samba with sudo /etc/init.d/samba start

After this I changed the workgroup on each of my windows systems to match and restarted.    Suddenly, everything is working!  Hope this helps.

---

### Post by coolnezz on 2009-10-04
i've been having problems connecting Ubuntu to Ubuntu PC.  I'm succesfull connecting Windows to Ubuntu and vice versa by disabling "encrypt password" set to false.  this solved my problem with Ubuntu to Ubuntu athentication:


Samba - solved - Re: smbclient failing: Server requested plaintext password... by John Riesen on 2009-07-07T02:03:24+00:00


You have to set 'client lanman auth = yes'.  Otherwise,
'client plaintext auth' is forced off.

So using 'smbclient -s foo.conf' where foo.conf has ...

[globals]
    client lanman auth = yes
    client plaintext auth = yes

... does the trick.

It seems this changed some time between 3.0.x and 3.2.x.

This bit of doco in smb.conf(5) in the 'client lanman auth'
section was the part I missed...

   Disabling this option will also disable the client plaintext auth
   option.

source link:

[http://www.pubbs.net/samba/200907/58086/](http://www.pubbs.net/samba/200907/58086/)


edit: I restarted SAMBA but it didn't work.
so I restarted the computer and everything worked!
oh well, still a newbie.

---

### Post by RealG187 on 2009-10-08
> **dmizer said:**
> The "Failed to retrieve share list from server" error is almost always firewall related. Try installing GUFW (via Synaptic Package Manager) and disabling the firewall in System > Administration > Firewall configuration.

Also, check Windows to make sure that no anti-virus or firewall is interfering on that end either.I get this error when trying to connect to my Windows 2000 VM and I have no firewall.

EDIT: Changing VirtualBox from NAT to bridged made the error go away. My physical network uses IPs like 10.0.1.x and when VBox was set to NAT the VMs got IPs like 10.0.2.x. I wonder if there were IP problems...

---

### Post by dunbrokin on 2009-10-31
I am getting this Mount Error problem on all 3 machines that we use in our house....none can talk to each other...though all have the same workgroup name. 2 of the machines are running Janunty and 1 is running Karmic.

Has anybody found a satisfactory solution to this problem yet?

---

### Post by RealG187 on 2009-11-02
I am getting this error in my 9.10 VM trying to connect to a Windows 7 host on both NAT and bridged. How do I make it work?

EDIT: I can manually type the path to a share (although I shouldn't have to) but when I transfer files it's really slow...

---

### Post by killfall on 2009-11-03
I am having similar problems. I have Ubuntu 9.10 running in VMware and have shared a folder on the Host pc using vmware tools but I am struggling to mount it. I am also running a VM of Win7 and have mounted the Shared folder in that fine.

If I try and connect to the windows network I get "Failed to retrieve share list from server", and if I try and mount the drive using

```
sudo mount -t vmhgfs .host/<folder> /mnt/hgfs
```with the shared folder name where <folder> is.
I get "Cannot mount file system : No such Device"

I'm fairly new to Linux

---

### Post by solva39 on 2009-11-04
I had the same problem and found a fix (not a workaround). Thought I'd share it with you guys. Below the link.

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by tock on 2009-11-04
I believe the quick and easy answer is to disable the firewall.  Although being a unacceptalbe answer for me, it does get file sharing working.  Now it's a matter of figuring out what iptables wants in order for filesharing to work..  I sure haven't found the answer.  Opening additional ports has got me at least seeing the other computers but I cant access anything on them.

edit. 
Elustran gave me a big piece of the puzzle.  He stated "I just fixed this problem on my 8.10 machine by opening up samba's ports on the gufw firewall (installable from Add/Remove) using TCP ports 139 and 445 and UDP ports 137-139. 137, 138, and 445 weren't open before. Also, I don't seem to have to open the nfs port for samba to work."  This allowed me to see my other computers but I still could not access the files.  I had to include the higher ports, 1025:65535, to get everything working right. If someone has a specific list of the higher ports that need to be included, please post.

---

### Post by RealG187 on 2009-11-05
> mpg@mpg-desktop:~$ sudo mount -t cifs //192.168.239.1/Share /home/mpg/Desktop/Host -o credentials=/home/mpg/.auth.winbox.mpg,noperm,uid=mpg,gid=mpg
mount error(12): Cannot allocate memory
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)Why's it doing this now? I tried rebooting and it still says it...

---

### Post by dmizer on 2009-11-06
> **RealG187 said:**
> Why's it doing this now? I tried rebooting and it still says it...

The only thing I can think of here is that this is a virtualization bug. For more information, take a look at this thread: [http://ubuntuforums.org/showthread.php?t=869994](http://ubuntuforums.org/showthread.php?t=869994)

---

### Post by RealG187 on 2009-11-06
I thought it was an issue with Ubuntu, but my Fedora VM had it too (I had the shares mounted and when I looked they weren't mounted and it did it when I tried to remount.

Since yesterday the host has been restarted and it's working now, it was something with the host...

---

### Post by Nachowarrior on 2009-11-17
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

okay, yeah, his post worked for me and is correct. One minor thing that most people o\/erlook when just starting to use linux (and i sometimes forget to look for too) is that it's all CASE SENSATI\/E! 

As soon as i capitalized my workgroup name in the smb.conf it worked fine. haha. So basically the default smb.conf has a mistake in it. I'm sure if this is the case (pun intended) for most people we can get them to push it out with the next update?

hope pointing this out isn't redundant on this thread and helps. :-p

---

### Post by digitalghost1 on 2009-11-21
> **sbyte said:**
> I get this happening to me a fair amount of time, however when it happens only the windows computers can talk to each other. when i do a "findsmb"
i can see:
my house mates XP laptop,
my 8.10 laptop,
and my 8.10 desktop (from which i am running the commands),
i cannot view my house mates XP Desktop.

if i open up the network in nautilus, i get the aforementioned "unable to mount location...."

my workaround is to open up FireFox, and enter "smb://192.168.0.199/", the location of my house mates XP laptop, which allows me to see the shares. 

once i can see the shares in FF, nautilus will allow me to browse them.

might work for you too :-)

This worked for me. I have two ubuntu 9.10 desktops.
I shared out one of the folders on one desktop but I cannot browse the Network and view the shared folder.

But, if I use the IP address and simple use Nautilus to navigate to "smb://192.158.0.100/" the desktop with the file share, now I can see it.

---

### Post by curtiswtaylorjr on 2009-11-29
I did not read all of the posts but I seem to have gotten it working by installing samba. I am using ubuntu 9.10+Studio RT kernel I have done this on 2 of my computers and seem to have resolved the issue. Hope this helps.:P

---

### Post by SedaliaSteve on 2009-11-29
Digitalhost1's method does work but I still can't get to it as a regular drive. This is on the client side. I have a Dell Mini 9.

Early this summer I started setting up a Ubuntu server based on a Shuttle XPC with RAID 1. It was originally 9.04 alternate distro and has been upgraded t 9.10. I set it up with a bunch of samba shared points so windows people in the house could mount drives to it and it works great for every windows box in the house or visiting, once addedd to the workgroup.

My laptop died during this and I replaced it with a Dell Mini 9 and it could see the computer and shares. I'd had an old Windows XP desktop with some shared drives and it was turned off during all of this. Once the server was working on a KVM switch I turned the old system back on and the Mini 9 has never had direct access since. I've taken it from the installed hardy to 9.04 to 9.10 with no luck. I turned off any type of firewall on it.

I'm not inclined to mess with the server since it works so well with everything else. It's the Mini 9 as a client that doesn't work.

Steve

---

### Post by Solomoriah on 2009-12-01
I'm running into this problem with several systems.  Here's the rundown:

Two computers are running Jaunty on quad core Intel hardware; one is a scratch install from a few weeks back, the other was upgraded from Hardy through Intrepid to get here.  A third computer is running Jaunty on an older Intel system, also scratch installed, and a fourth is an Acer Aspire One with UNR Karmic on it, installed yesterday.

None of the above systems can see the server list in Nautilus (or open the Windows Network icon), EXCEPT the quad core that was scratch built with Jaunty.  It has a slightly different smb.conf, but I've changed the other quad to match it in terms of global configuration, and this hasn't helped.

Both quads have Samba installed; neither the netbook nor the older machine do.  But note that one quad sees the server list, the other does not, so I don't see how this is relevant.

I tried the nsswitch.conf change on the netbook and the problem quad, and got very strange results... on the netbook, the shares for the only Windows machine on the network show up (the shares, not the server) in the network:/// listing, along with the Windows Network icon, but none of them work (all giving the same "Failed to retrieve share list" message).  On the quad, I see its own shares as if they were servers, and again neither they nor the Windows Network icon will open.

None of these computers have firewalls running (never bothered to install them).  I've been through the entire list of changes proposed by dmizer in the other thread, and except for the very broken behavior described above for the nsswitch.conf changes, I didn't see a bit of benefit.

But one computer works, for no apparent reason.

---

### Post by Solomoriah on 2009-12-03
Okay, here's an update:

The system I mentioned above where the Network window works, well, it sort of works... that system shows all the computers in the workgroup, but the Windows Network icon gives the "Unable to mount location" message as in the title of this thread.

Another system on my network is an older unit, running Jaunty but upgraded from Hardy through Intrepid (not scratch installed).  It also cannot see workgroup computers nor open the Windows Network icon.

Is it too much to ask that the error message actually tell us something?

Or even, that it work?

My wife had a cow over this.  She's given me hell for upgrading from Intrepid, where this just worked.  Is anyone actually trying to fix it?

---

### Post by 888guy on 2009-12-03
I've been horsing with this for about an hour....  I found the solution:  reinstall Slackware - which I've been using for about 5 years and which involves virtually none of this sort of nonsense.   Whew.  If the goal of this endeavor (the Ubuntu project) is to create a Linux distribution which is geared for the average computer user they're certainly "losing the plot", as the Brits say....  I run a computer repair shop and had actually been suggesting this distro to customers who'd been plagued by viruses.  Then  I find that you have to go on a forum and jerk around, like this, to make this thing see a Windows share or another Linux share!  Good luck, Ubuntu Project.

Making network shares easily accessible should be a priority in a Linux distro aimed, largely, at home users and hobbyists.  This is completely whacky.  Good Lord, Slackware - straight out of the box - requires a simple edit to /etc/inetd.conf to enable swat and an equally simply edit to the /etc/rc.d/rc.local file to start samba at boot.  And, then, all of your Windows and Linux shares are accesible in much the same way that they are on Windows.  

I'm outta here, folks.

---

### Post by sevenearths on 2009-12-11
> **nsew said:**
> ...

A bit more digging around, and I found another post [http://forums.linuxmint.com/viewtopic.php?f=157&t=24407]("http://forums.linuxmint.com/viewtopic.php?f=157&t=24407"), shrugged my shoulders, and installed smb4k. Though this didn't seem to change anything when trying to browse the network.

After, I noticed the Connect to Server option. So, going to Places -> Connect to Server -> Service type = Windows Share. Filled in the details, and now I have the folders mapped, and appearing under Places. 

Additionally, I can browse via Nautilus without using the shares, as mentioned in one of the quoted sections.

Again, I understand this isn't a proper fix, and I'm rather clueless, but I thought to share my experience nonetheless. 

Will

THANK YOU!!! THANK YOU!!! THANK YOU!!! 

Places -> Connect to Server -> Service type = Windows Share

solved the problem for me  :D:D:D

---

### Post by Solomoriah on 2009-12-11
The bug filed against this problem assigns it a priority of "low" and calls it an upstream problem; I can't find any similar bugs in the GNOME Bugzilla system, so it appears it hasn't been filed there.  But, I'm having trouble figuring out what the current gvfs version actually is, and if we are using it or not... that could easily make a difference.

Does anyone else find the GNOME development sites confusing?

---

### Post by billfinch on 2009-12-15
I agree with 888guy. This just should not be that hard. Having said that and having just spent 3 weeks getting my wireless to work, I took the path of least resistance on this Windows network issue. Given the number of posts, I now know that there is probably no solution for everyone no matter how hard you look.

I'm running Hardy. At one point, when I was wired up and before the wireless was fixed, I actually had Nautilus browsing my network as it should. Once I knew to put the workgroup name = my workgroup  in smb.conf and to use the Connect to Server > Windows Share etc. with the Domain Name = my workgroup, I was all set.

That all changed when I had to reinstall to get wireless up. Dead in the water with the "Can't retrieve windows share" message. Simplest way around this is Digitalghost1's approach. Put smb://IP address of the machine you want to navigate to in the Location line of Nautilus and away it goes. Bookmark it and give it the server name. Same for any other machines. I only have 2 and as long as my network doesn't reboot, I'm good to go.

Onward to network printers.....:)

---

### Post by Paper Pusher on 2009-12-24
I am the latest in a long line of frustrated Ubuntu users. Here I am on Christmas eve posting instead of enjoying my wassail.

My home wired 100Mb network has 

o 32 and 64-bit machines running 
 64-bit Ubuntu 9.10 and 8.10
 32-bit 9.10
 32-bit Windows XP
o a network camera
o an internet connection
o a NAS drive

The XP machines can see everything.
The Ubuntu machines used to be able to see everything until 4 weeks ago.  They saw the NAS drive though Places> Network...  Everything else they saw and currently see through the Firefox browser.

For about 4 weeks now, none of the Ubuntu machines see the NAS drive.  They get the "Cannot retrieve..." error instead.

What changed?
This used to work.

---

### Post by Paper Pusher on 2009-12-25
A lot of the solutions call for the NAS drive's internet address. How do I find that out?

---

### Post by Solomoriah on 2009-12-25
I got my network functioning again.  Apparently, I needed one of my Ubuntu systems to be the master browser; I added the following to the smb.conf file on my primary office computer (inventively named "office"):

```
   local master = yes
   preferred master = yes
   os level = 35
```
I added those lines to the global section (the part before the first share definition) and within a few hours all the computers on the network were happy... the Windows Network worked right away, but actually seeing the workgroup computers in the network:/// view took a while.

---

### Post by Woobus on 2010-01-01
Hello, first time poster.

I'm using 9.10 (Karmic Koala) and just solved this issue, using dmizer's excellent HowTo post:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

I just started at the top, tested after each fix, and kept going until I could connect.  For me, it was the solution - **Problem 3, Part 1** that fixed it.

---

### Post by xjgnsdof on 2010-01-06
> **sevenearths said:**
> THANK YOU!!! THANK YOU!!! THANK YOU!!! 

Places -> Connect to Server -> Service type = Windows Share

solved the problem for me  :D:D:D

Solved it for me, too. Gives me the convenience of a bookmark in Nautilus to boot.

---

### Post by jmf1086 on 2010-01-15
If you still are have problems I found this tutorial to be nice and helpful, it helped with the one step I did not think about my Windows 7 sharing set up. 
[http://www.randyjensenonline.com/blog/connect-ubuntu-810-windows-7-share](http://www.randyjensenonline.com/blog/connect-ubuntu-810-windows-7-share)
enjoy

---

### Post by gdwilson9 on 2010-01-16
> Paste this line 
" name resolve order = lmhosts wins bcast host "
into the smb.conf file under this section: 

# What naming service and in what order should we use to resolve host names
# to IP addresses
 ; name resolve order = lmhosts host wins bcast" .

Put this in the command line to edit the file.
sudo gedit /etc/samba/smb.conf
 
Save the file, log off and back on.

Kudos to DaleKonley on June 11th, 2009.  This worked for me.

---

### Post by filigran on 2010-02-07
> **gdwilson9 said:**
> Kudos to DaleKonley on June 11th, 2009.  This worked for me.

Just thought I'd verify this solution .It also solved the same issue for me, on a Gentoo system.

---

### Post by cyber_rigger on 2010-02-17
> **DaleKonle said:**
> This is an easy fix that worked for me. Change the resolve order.
 
Paste this line 
" name resolve order = lmhosts wins bcast host "
into the smb.conf file under this section: 

# What naming service and in what order should we use to resolve host names
# to IP addresses
 ; name resolve order = lmhosts host wins bcast" .

Put this in the command line to edit the file.
sudo gedit /etc/samba/smb.conf
 
Save the file, log off and back on.

See:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/375593](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/375593)

**[COLOR=Blue]Here's what worked for me[/COLOR]** with Ubuntu Karmic

**HOWTO browse Windows shares with Ubuntu;**

Edit [COLOR=DarkRed]/etc/samba/smb.conf[/COLOR]

Change the line:

**;   name resolve order = lmhosts host[COLOR=Red] wins[/COLOR] bcast**

so that 'wins' comes first or second

i.e.

[B]resolve order = [COLOR=Red]wins[/COLOR] lmhosts host bcast 

or

[/B]**resolve order = lmhosts [COLOR=Red]wins[/COLOR] host bcast **

On my debian machine I instal[COLOR=Black]led[/COLOR]**[COLOR=Black] [COLOR=DarkRed]winbind[/COLOR][/COLOR]**

---

### Post by jruberto on 2010-03-02
doh.

---

### Post by unpresedented on 2010-03-23
> **cyber_rigger said:**
> **[COLOR=Blue]Here's what worked for me[/COLOR]** with Ubuntu Karmic

**HOWTO browse Windows shares with Ubuntu;**

Edit [COLOR=DarkRed]/etc/samba/smb.conf[/COLOR]

Change the line:

**;   name resolve order = lmhosts host[COLOR=Red] wins[/COLOR] bcast**

so that 'wins' comes first or second

i.e.

[B]resolve order = [COLOR=Red]wins[/COLOR] lmhosts host bcast 

or

[/B]**resolve order = lmhosts [COLOR=Red]wins[/COLOR] host bcast **

On my debian machine I instal[COLOR=Black]led[/COLOR]**[COLOR=Black] [COLOR=DarkRed]winbind[/COLOR][/COLOR]**

when I try to edit this file it says you do not have sufficent privileges to save the file, what should i do (im new comer to Linux) ?

---

### Post by Solomoriah on 2010-03-23
You need superuser access.  I'm assuming  you don't use vi, since you are a newcomer; so probably you'll want to use gedit.  From a terminal window, enter this command:

sudo gedit /etc/samba/smb.conf

You'll be prompted for your password, and then the file will open.  Be careful editing it.

---

### Post by drewsus on 2010-04-17
> **DaleKonle said:**
> This is an easy fix that worked for me. Change the resolve order.
 
Paste this line 
" name resolve order = lmhosts wins bcast host "
into the smb.conf file under this section: 

# What naming service and in what order should we use to resolve host names
# to IP addresses
 ; name resolve order = lmhosts host wins bcast" .

Put this in the command line to edit the file.
sudo gedit /etc/samba/smb.conf
 
Save the file, log off and back on.

See:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/375593](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/375593)


This fixed the issue for me, thanks!

---

### Post by fielious on 2010-05-01
I don't know if this was solved yet but the problem is with DNS.
when you browse the network the smbclient knows the host name of your smb share. So when you click on the server it goes to your dns server and looks for the hostname.  if your host name is not in your dns then it will fail

update.
sorry for the reply before reading more into it.  The problem is still a mater of resolving names to ip addresses.

---

### Post by chadlongstaff on 2010-05-02
> **fielious said:**
> I don't know if this was solved yet but the problem is with DNS.
when you browse the network the smbclient knows the host name of your smb share. So when you click on the server it goes to your dns server and looks for the hostname.  if your host name is not in your dns then it will fail

update.
sorry for the reply before reading more into it.  The problem is still a mater of resolving names to ip addresses.

forgiven for your reply without reading, clearest post on here, added my network devices' IP and name to /etc/hosts and all is good with it again. a wonderful first cup of Ubuntu :lolflag:

---

### Post by Tonyaude on 2010-05-02
Totally agree with 888guy. Played with version 9.10 and couldn't get that to access windows shares. Have been trying for 3 days now with v 10 and have followed and actioned the suggestions in this thread and more!!! Still not working. No problem accessing the Ubuntu from Windows 7. Like others here I'm trying to help people reduce costs by using alternatives to Microsoft, but until things like this work straight out of the box there's no chance to persuade people. An URGENT quick fix is required or like 888guy I'm outa here and will also certainly NOT recommend a move away from Windows.

---

### Post by dannyboy79 on 2010-05-03
> **Tonyaude said:**
> Totally agree with 888guy. Played with version 9.10 and couldn't get that to access windows shares. Have been trying for 3 days now with v 10 and have followed and actioned the suggestions in this thread and more!!! Still not working. No problem accessing the Ubuntu from Windows 7. Like others here I'm trying to help people reduce costs by using alternatives to Microsoft, but until things like this work straight out of the box there's no chance to persuade people. An URGENT quick fix is required or like 888guy I'm outa here and will also certainly NOT recommend a move away from Windows.
i use the /etc/hosts file for my name resolution on the machines trying to access the SMB or SAMBA shares. then within my smb.conf on the server i have this line:

name resolve order = lmhosts host wins bcast

i also have this in my /etc/nsswitch.conf file

hosts:          files hosts wins dns

DONE!!!

P.S. On windows you edit the LMHOSTS file.

So bottom line is that if you can't access your shares on your windows computer by hostname, try by ip address.

smb://win7_ip_address/share

see what happens. the other poster was correct, if you don't have a REAL dns server in your router or even a half way decent consumer router, it may not work because it can't relate the ip to the hostname.
Oh and if you can't get it or think it's too difficult, dont suggest Ubuntu to others and be my guest and go back to paying $300 for your OS and who's knows how much for various apps.

Peace out....

---

### Post by JimFuqua on 2010-05-13
I don't know much about samba or the details of how Linux works and struggled with this problem for several hours.

In the end I found that the problem was a firewall.

I removed ufw and firestarter and it solved my samba problem.

Will the removal cause other problems?  There is a linksys router between the computer and the Internet.

Jim Fuqua

---

### Post by fuzz500 on 2010-05-13
Like Dannyboy was saying, I revised the name resolve order in smb.conf
AND the hosts line in nsswitch.conf... AND I installed winbind.

I am revising this post. This did NOT TOTALLY work for me. But it did
help. I did several installs of Lucid and they
could not see samba shares on each other, but the windows machines (xp)
on the network could see and manipulate shares on the Ubuntu machines.

I changed the name resolve order in /etc/samba/smb.conf (I put wins at the beginning)
   name resolve order = wins lmhosts host bcast

AND
change the hosts: line in /etc/nsswitch.conf
from
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
to
hosts:          files hosts wins dns mdns4
AND
installed winbind with synaptic. rebooted everything.
and it mostly worked.

File sharing this way is very inconsistent. After rebooting
everything several times, everything worked as expected. There
seems to be some issues with network discovery. 

This is really a problem for wider acceptance of Ubu
in a heterogeneous computing environment... i.e. the real world.
Not everyone has the time to tinker with things until they work.

my 2 cents.
Fuzz

---

### Post by milesrlv on 2010-05-15
I am having the same problem and have been trying to get it to work for two weeks and have not found anything that works. It has been about 5 years since I last used Any Linux version and I don't recall this even being a problem. I don't think anybody out there knows the cause of the problem because if they did it would have been solved by now and put to bed permanently. Up to this point I was absolutely in love with this distro but my patience can only last so long. I can not see any shares whether they are windows or Ubuntu/Linux.

---

### Post by EvilSmith on 2010-05-17
[SIZE=2]I think I got it working guys...  This worked for me to browse my windows based machines with Ubuntu (Debian)

Here is what I did:

1.  Edited the smb.conf using    sudo gedit /etc/samba/smb.conf

          workgroup = yourworkgroupname
          server string = %h
          netbios name = computername
          wins support = yes
          ;   wins server = w.x.y.z 
          dns proxy = no
          ;   name resolve order = lmhosts wins bcast host (notice the "host" is last)
#### Networking ####

;   interfaces = 127.0.0.0/8 eth0

;   bind interfaces only = yes
####### Authentication #######

   security = SHARE (changed this from user to share)
   encrypt passwords = no


Save the file

2.  Edited the nsswitch.conf using      sudo gedit /etc/nsswitch.conf
     
        find this line 
         
              hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

        and change it to
         
              hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

Save the file

3. Install winbind

sudo apt-get install winbind

REBOOT YOUR MACHINE

AND YOU'RE DONE !!!

Oh yeah...  Previously b4 this problem was occuring I installed apache bc i wasn't able to share files with Nautilus and 
don't know if it changes samba's behavior in any way but I'm sure everybody has it installed anyway. 

You might have to wait till Nautilus scans the network to show all the machines on your network but as soon as you see them they are browsable with no delay :)
This worked for me and I hope it does for you guys[/SIZE]

---

### Post by ktritty on 2010-05-18
> **Tonyaude said:**
> ...but until things like this work straight out of the box there's no chance to persuade people. An URGENT quick fix is required or like 888guy I'm outa here and will also certainly NOT recommend a move away from Windows.

There is no need to get all puffed up or one-dimensional about these things.  We live in a supposedly free market, with many products from which to choose.  If you want an OS that is somewhat more turn-key and mainstream when it comes to not needing to really understand the workings of a computer, then Windows is your best fit (That is perfectly fine- I drive a car all the time and care very little about its inner workings.)  It does not mean that you should tell everyone you know to stay with Windows.  Macintosh is by a longshot the best fit for my needs, there is no need arguing that with me.  But I won't arm wrestle you into switching to Mac.  The fact is, if you want an operating system that truly gives you control over every aspect you can imagine, and at a very, very low operating cost once you know how to use it, then Ubuntu is perfect for you.  It does not always work perfectly out-of-the-box because that is not what this is for.  It is intended to have reasonable default settings that give good chances of working, but allow you to change it as needed to make it perfectly optimized (even at the kernel level, which you cannot readily touch in Windows) for your needs.

The switch from Windows to Linux can be quite a leap.  The only way that I survived the switch with most of my hair intact was dual-booting.  It sounds like you are comfortable with Windows.  There is nothing intrinsically wrong with that.  But if you want to have say a server set up for various services, and never, ever be forced into upgrading or changing hardware, or dealing with security issues, than you should consider Ubuntu, but know that there is no instant gratification, and it will come with a learning curve just like anything else in this world that is worth learning.

---

### Post by warfie on 2010-05-21
hmmm... not sure what exactly did the trick because I ignored the advice to reboot, thinking that restarting samba would be enough. I tried everything suggested in this thread and eventually had to reboot for another, unrelated issue, now everything is good...

Just thought I'd share that for anyone else who thinks as I did 


[DOH]

---

### Post by picbits on 2010-05-21
I've just been trying to solve a similar problem: 

Heres the scenario

6 machines on Windoze from 2k to 7
2 servers (one new server on the network to decomission the old one)
1 Myth Frontend (Revo)
All running Samba

Now ........

The Revo could see all machines
The Windows machines could see all machines
The old server could see all machines
The new server would only see random machines and would not access shares on them. Network browsing was slow and would take 30-40 seconds before it times out.

Disabled samba server on old server - new server now browses other machines without a problem and browsing is fast.

Set old server smb.conf to no be master browser - restarted samba on both machines and same problem - slow network browsing and unable to access shares from new server.

Ping the revo machine by name - no results
Ping the laptop by name - no results
Ping other computers by name - no results
Ping the old server by name - get external network fixed ip address ......... ding

Now the old server could be pinged by the name pbserver. This however resolved as the external IP address of my network (i.e. my DSL Router IP). My netbios name was pbserver as well.

I changed the server netbios share name in smb.conf on the old server to "pbshare", restarted samba and everything worked perfectly (and still is)

So ...... if you can ping the name of your share and it doesn't resolve to the internal network IP address of the machine then it might be worth changing the share name of the machine.

My theory was when the network browser was trying to locate the old server, it was hitting the router IP rather than the actual machine itself.

Speculation and I'm a bit of a Linux novice but worth considering.

---

### Post by Peteb1951 on 2010-06-11
> **EvilSmith said:**
> [SIZE=2]I think I got it working guys...  This worked for me to browse my windows based machines with Ubuntu (Debian)

Here is what I did:



Thanks Evil, this worked immediately for me using Eeebuntu (based on 9.04) on an EeePC 901. I am now able to look at the shares on my Linkstation NAS.

---

### Post by aalhamer on 2010-06-29
I faced the same problem in Ubuntu 10.04. After updating my Media PC [from 9.04 to 10.04], Samba just did not mount on any other PC on my network.

The problem is in the Preference Settings. Just go to [Preference-> Server Settings-> Security] Make sure the [Authentication Mode] is on (Share), and that the [Encrypted Password] is (off), also set the {Guest Account] under the (Media PC Account).

That should do it

---

### Post by Sugi on 2010-07-06
EDIT: I have tested this method again and got even better results.
Test #2
I have ran the below method on my ubuntu 9.10 86x and got better results. but I am still running into the same problem, once this method is in place and installed, windows xp can't see the ubuntu machines.  Any clues on how to fix this?  

All I had to change this time was:
> 
Install winbind
sudo apt-get install winbind

/etc/nsswitch.conf
  hosts: files mdns4_minimal [NOTFOUND=return] wins dns mdns4

Edit /etc/samba/smb.conf  [I don't think this part is needed.]
   workgroup = WORKGROUP


Test #1
I can't get my ubutnu 9.10 64x computer to be seen by windows xp.  The method below will enable ubuntu to see windows (xp).  Test #1, method used below:

Method by EvilSmith.
1. Edited the smb.conf using sudo gedit /etc/samba/smb.conf
> # Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
   netbios name = USERNAME

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = yes

# What naming service and in what order should we use to resolve host names
# to IP addresses
; name resolve order = lmhosts wins bcast host

2. Edited the nsswitch.conf using sudo gedit /etc/nsswitch.conf
> 
hosts: files mdns4_minimal [NOTFOUND=return] wins dns mdns4

3. Install winbind
sudo apt-get install winbind

4. sudo service samba restart
Everything should work after this

Specs:
ubuntu 9.10 64x (See Windows XP 32x & Ubuntu 9.10 86x)
Windows XP 32x (can't see Ubuntu 9.10 64x or Ubuntu 9.10 86x)
Ubuntu 9.10 86x (See Windows XP 32x & Ubuntu 9.10 86x)

Thanks,
Sugi

---

### Post by amg on 2010-07-17
Just a quick note, I had the same problem as above, apparently Gnome forgot that I was part of the workgroup "WORKGROUP", a quick fix in gconf (/system/smb/) and everything was alright.

Though it seems that this error message is related to numerous problems.

---

### Post by Urhixidur on 2010-07-20
One very important thing that needs to be done, once you've got your workgroup and firewall issues worked out, is to make sure the /home/username folder has execute permission for all (chmod a+x /home/username).  This is not mentioned enough in the forums and will lead to the "Unable to mount location" message if not done.  Oh, and the shared folder must itself have a+rwx permissions if you want it to work right (a+rx will give you a read-only folder).

---

### Post by dmizer on 2010-07-20
> **Urhixidur said:**
> (chmod a+x /home/username).

This is an exceptionally bad idea and can break things.

The best thing to do is to dedicate a single folder to sharing instead of sharing your entire home directory. Sharing your home directory exposes your desktop settings and history to the entire network, and chmodding them to a+x allows anyone, anywhere, to modify and view them (including things like browsing and terminal history).

---

### Post by Urhixidur on 2010-07-22
> **dmizer said:**
> This is an exceptionally bad idea and can break things.

The best thing to do is to dedicate a single folder to sharing instead of sharing your entire home directory. Sharing your home directory exposes your desktop settings and history to the entire network, and chmodding them to a+x allows anyone, anywhere, to modify and view them (including things like browsing and terminal history).

You misunderstand.  I am not sharing my home directory (that would be a bad idea indeed).  To be specific, I dedicated $HOME/Public to sharing and published it through Samba, but it turned out to be unreachable from other machines in the workgroup (network:/// would show Windows Network, then the Workgroup inside it, then the machines inside that, but my machine was not mountable).  This was fixed by changing the permissions for HOME$ from drwx------ to drwx--x--x.  Surely that cannot allow the contents of $HOME to be read or modified?

---

### Post by dmizer on 2010-07-22
> **Urhixidur said:**
> You misunderstand.  I am not sharing my home directory (that would be a bad idea indeed).  To be specific, I dedicated $HOME/Public to sharing and published it through Samba, but it turned out to be unreachable from other machines in the workgroup (network:/// would show Windows Network, then the Workgroup inside it, then the machines inside that, but my machine was not mountable).  This was fixed by changing the permissions for HOME$ from drwx------ to drwx--x--x.  Surely that cannot allow the contents of $HOME to be read or modified?

I'm sorry if I misunderstood, but you didn't say anything about a Public folder in your previous post, you only mentioned /home/username. Even if you are not sharing everything in /home/username, it's still a bad idea to change the permissions on the entire directory, and an even worse idea to change the permissions of /home. You should only change the permissions on the shared directory itself.

---

### Post by dogugotw on 2010-07-31
> **macromike said:**
> I'm not sure if this will help, but I was having the same problem and it turned out that the firewall in ubuntu was blocking the netbios ports (TCP port 139) needed to make name resolution work properly when browsing the windows network.

I solved it by installing & running gufw (gui for uncomplicated firewall) and going to the Preconfigured tab to tell it to allow the netbios-ssn service and the nfs service.

Thank you.  This fixed my issue perfectly.  Somewhere along the line I must have turned on the firewall but failed to configure it properly.  I can now see my network shares!

---

### Post by Urhixidur on 2010-08-02
> **dmizer said:**
> I'm sorry if I misunderstood, but you didn't say anything about a Public folder in your previous post, you only mentioned /home/username.

True.  I should have made it clear I was considering the (usual) case of a Public sub-folder of $HOME.

> **dmizer said:**
> Even if you are not sharing everything in  /home/username, it's still a bad idea to change the permissions on the  entire directory, and an even worse idea to change the permissions of  /home. You should only change the permissions on the shared directory  itself.

Unfortunately, that is not what Samba expects.  Samba forced me to give execute permission on the shared folder's container (i.e., $HOME).  In order to make $HOME/Public mountable by remote machines, $HOME must have execute (x) permission for all (assuming anonymous/public access).  Or have you been able to get Samba to work (that is to say, to have a mountable $HOME/Public folder) without setting $HOME's permission to a+x?

---

### Post by Solomoriah on 2010-08-02
If you are using a "force user" permission, you might be able to avoid the X permission.  However, if you are granting R permission to "other" anyway, X won't hurt anything.

I'd be using "force user" myself.

---

### Post by Urhixidur on 2010-08-10
> **Solomoriah said:**
> If you are using a "force user" permission, you might be able to avoid the X permission.  However, if you are granting R permission to "other" anyway, X won't hurt anything.

I'd be using "force user" myself.

I'm afraid I don't understand.  What is "force user"?

---

### Post by Solomoriah on 2010-08-10
If you actually want to make a folder within your home directory public, you should either:

1.  Make the folder fully world-writable, or
2.  Use the "force user" directive to make the user connecting "equivalent" to you.

I.E.:

[joespublic]
    path = /home/joe/public
    force user = joe
    ... other directives as appropriate ...

You might also want to use "force group" in some situations.

---

### Post by heviiguy on 2010-08-25
:D ***[COLOR=DarkGreen]Hah! Finally "fixed" it!! [/COLOR]***

After having set-up Samba and shared folders and all of the other stuff suggested in the myriad posts concerning this _horrendous problem_, this is what I did:


[LIST]
[*]determined the IP address of each of my two computers on the network
[*]opened Nautilus
[*]entered the IP address of the second box thus: **smb://192.168.0.245** in Location (ie: **GO, Location**...)
[*]fell off of my chair when I saw all of my shared files on the second box
[*]*quickly* added this location as a Bookmark ;)
[*]did the same on the second box with the exception, of course, of entering the IP address of the first box in Location
[/LIST]

Just for the heckuvit, I opened the lmhosts.conf file ( **gksudo gedit /etc/samba/lmhosts.conf** ) and entered 
[B]192.168.0.245   BOX-1
192.168.0.251   BOX-2[/B]
Thought that this would resolve the issue of Nautilus only recognizing the IP addresses and not the box names. Didn't make a difference ](*,). No problem though because now I just have to select the appropriate bookmark in Nautilus and, Bob's my uncle! :guitar:

---

### Post by dmizer on 2010-08-25
> **heviiguy said:**
> :D ***[COLOR=DarkGreen]Hah! Finally "fixed" it!! [/COLOR]***

After having set-up Samba and shared folders and all of the other stuff suggested in the myriad posts concerning this _horrendous problem_, this is what I did:


[LIST]
[*]determined the IP address of each of my two computers on the network
[*]opened Nautilus
[*]entered the IP address of the second box thus: **smb://192.168.0.245** in Location (ie: **GO, Location**...)
[*]fell off of my chair when I saw all of my shared files on the second box
[*]*quickly* added this location as a Bookmark ;)
[*]did the same on the second box with the exception, of course, of entering the IP address of the first box in Location
[/LIST]

Just for the heckuvit, I opened the lmhosts.conf file ( **gksudo gedit /etc/samba/lmhosts.conf** ) and entered 
[B]192.168.0.245   BOX-1
192.168.0.251   BOX-2[/B]
Thought that this would resolve the issue of Nautilus only recognizing the IP addresses and not the box names. Didn't make a difference ](*,). No problem though because now I just have to select the appropriate bookmark in Nautilus and, Bob's my uncle! :guitar:

There are a few of problems with this, and why it is not offered as a real workaround. First, most LAN networks are DHCP which means that your IP addresses change, so it will work fine until you reboot or your IP lease expires. There are ways around this, but it requires you to configure your LAN for static IP, or configure your router to assign permanent IP leases based on MAC address, and not all retail routers have this capability. Second, bookmarking the share in Nautilus works fine unless you need to open a file with a program that does not have Nautilis awareness like Open Office, and a number of popular music players.

---

### Post by heviiguy on 2010-08-25
pfffffffttttttttt....  (that's the sound of the air being let out of my big happy balloon)

Yeah, I now see what you mean about the dynamic nature of IP addresses. Furthermore, not being able to access my networked boxes via other applications is also a problem. 

Since I've yet to come across a solution to this apparently ubiquitous issue, does my "non-solution" at least provide a springboard for somebody much more astute in things Ubuntu to perhaps look at this in a different light?

---

### Post by keithspg on 2010-08-25
Reading this thread with interest. I think the problem is the password issue that has never been truly fixed. It seems to be related to the domain shares versus regular windows shares. 

Currently, I cannot view any shares on the Workgroup domain except of my machine on on my machine. Samba is properly configured and will list all the shares on the network. It appears to be either Nautilus or gvfs as I can see and browse all shares that are on my domain, but cannot browse any of the 'Workgroup' shares at all. The windows boxes browse them happily. Also, if I launch XP in a vbox on my machine, it can browse all of them happily as well. It appears that it is the 'basic network shares' which it has the problems with. Also I cannot browse obex shares either even though those are also properly configured and visible from the command line. If I were to guess, it is a gvfs deal.

Keith

---

### Post by nlsgs on 2010-08-30
Hi,

I had a similar problem like "server not visible in domain, but if you knew the name and share you could simply access it" even on the invisible server (from Ubuntu 8.10). Win98 was completely lost; mounting a network drive did not work,  printing failed.
WinXP worked, but installing a new printer failed.
When altering the /etc/samba/smbd.conf file you have to restart smbd (using **sudo service smbd restart)** . Then I remembered that in the old days there where two daemons you had to run, smbd and nmbd. When I checked I found that nmbd was not running. So I did **sudo service nmbd start** and all worked as normal again.

I do not know:
= what nmbd does
= why how and what stopped it (system update?)
= if it now restarts at system reboot

But for now it is a giant step forward.
Regards,

Simon

---

### Post by Solomoriah on 2010-08-30
nmbd provides name services; smbd provides print and file services.  Without a running nmbd, your computer can only be found by IP address.

Probably that's an oversimplification, but it'll do for now.  As to why yours was down, that'd be speculating.

---

### Post by wd5jhi on 2010-11-21
Go to the '/etc/samba/smb.conf' file on the server and change the two lines below.  That fixed it for me.  PRAISE GOD!


#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0
   interfaces = eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes
   bind interfaces only = yes

---

### Post by thinkinhurtz on 2010-12-02
OMG heviiguy you just fixed my problem thank you!
Was getting the error:
Unable to mount location
Failed to retrieve share list from server
Solved in Firefox with smb://192.168.1.xxx/folder

---

### Post by jamied_uk on 2010-12-28
i can see the computers on linux and windows but i cant login using ubuntu a windows share and i cannot get into ubuntu from windows without a access error any fix for this i am using mint 9 :d thanks

---

### Post by EvilSmith on 2011-01-06
> **jamied_uk said:**
> i can see the computers on linux and windows but i cant login using ubuntu a windows share and i cannot get into ubuntu from windows without a access error any fix for this i am using mint 9 :d thanks

What version of Windows are you using ?

---

### Post by jamied_uk on 2011-01-06
it was windows xp (can multi boot with linux)  and when i did authenticate with linux and windows xp, because of a dodgy patch cable it currupte my conection with other pcs including my linux, now i have reinstalled it has wiped my drive so i am recovering with ntfs get data back program. :/

---

### Post by EvilSmith on 2011-01-06
> **jamied_uk said:**
> it was windows xp (can multi boot with linux)  and when i did authenticate with linux and windows xp, because of a dodgy patch cable it currupte my conection with other pcs including my linux, now i have reinstalled it has wiped my drive so i am recovering with ntfs get data back program. :/


So I understand your connection was corrupt because of a bad network cable.  Did you fix the problem after ?  

If not and you don't want to edit smb.conf files etc as I posted earlier you should upgrade to Ubuntu 10.10 which seems to be preconfigured so it has these issues fixed between Windows and Ubuntu. I have it installed on my Lappy and with original configuration I use it at work, home and friends' places and I never have any problems accessing Windows shares.:p

---

### Post by {VeXeD} on 2011-01-23
I just wanted to say thanks to dmizer. If you follow his link, unless you have soem odd non-typicle setup, you will find the problem. I think it was link 6 option 5 that ended up doing it for me.  :KS :KS :KS :KS stars 4 u demizer.

---

### Post by wesswei on 2011-01-24
Here is the bug in launchpad: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/481197]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/481197")

Everyone please go here and report the same problem. They may not care to fix issues with samba, but if enough people do, then someone will take then hint!

---

### Post by Morbius1 on 2011-01-24
If it's presented as a problem with Samba it will never get fixed. Ubuntu will pass it to the Samba folks and it will end up in File13 since from their perspective Samba ain't broke. If you can access the remote share by ip address and not by host name then it's not a Samba problem it's a network problem ( i.e. name services ).

It could also be a firewall problem or a host name length problem. It may also be a problem with Nautilus, or with gvfs, or maybe even fuse but I suspect it's not Samba. Don't get me wrong a misconfigured smb.conf file can break things and smb.conf itself can be used to fix certain things ( You wouldn't believe how many times changing the name resolve order to list bcast first has fixed this problem since it's the only method that is functional out of the box).

Even changing the router has shown to fix this problem.

---

### Post by capscrew on 2011-01-24
> **Morbius1 said:**
> If it's presented as a problem with Samba it will never get fixed. Ubuntu will pass it to the Samba folks and it will end up in File13 since from their perspective Samba ain't broke. If you can access the remote share by ip address and not by host name then it's not a Samba problem it's a network problem ( i.e. name services ).

It could also be a firewall problem or a host name length problem. It may also be a problem with Nautilus, or with gvfs, or maybe even fuse but I suspect it's not Samba. Don't get me wrong a misconfigured smb.conf file can break things and smb.conf itself can be used to fix certain things ( You wouldn't believe how many times changing the name resolve order to list bcast first has fixed this problem since it's the only method that is functional out of the box).

Even changing the router has shown to fix this problem.

A BIG +1 to @Morbius1's thoughts.  The fact that you can't connect by name is not a bug, rather it is a misconfiguration or lack of correct configuration of Samba.

---

### Post by Balthazar_Droid on 2011-02-09
> **wd5jhi said:**
> Go to the '/etc/samba/smb.conf' file on the server and change the two lines below.  That fixed it for me.  PRAISE GOD!


#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0
   interfaces = eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes
   bind interfaces only = yes

Thank-you!! This fixed my exact problem!!

---

### Post by dmizer on 2011-02-10
To anyone experiencing this error:

According to this post: [http://ubuntuforums.org/showpost.php?p=10405454&postcount=490](http://ubuntuforums.org/showpost.php?p=10405454&postcount=490) a problem on the Windows side of things could be causing it.

Windows fix noted here: [http://support.microsoft.com/kb/177078](http://support.microsoft.com/kb/177078)

---

### Post by stoian on 2011-03-02
SOLVED

This did it for me:
[http://ubuntuforums.org/showpost.php?p=7790197&postcount=43](http://ubuntuforums.org/showpost.php?p=7790197&postcount=43)

The netbios name in my smb.conf was not the machine name...

---

### Post by stoian on 2011-03-02
):p

---

### Post by love2learn on 2011-04-14
I just had this problem. These are the circumstances and how I (apparently) fixed it:

The file Server is Ubuntu Server 10.04
The media center has Ubuntu Desktop 10.04
They were connected via a router

Media Center could not connect to Server after a week of successful connections. 

What I believed happened is I turned off and unplugged the server from the router for some unexpected maintenance. The media center stayed on as I did not think/need to take it down. When I got the server back up the media center "Failed to retrieve share list... " I restarted the media center and figured everything would be fine. Nope, couldn't connect. I could see the Server via entering the smb://192.168.1.10/Movies but any other way would not work. 

Basically all I did was turn off all my linux computers that had Samba on it and then restarted the Server. ( I tried "sudo restart smbd" first but that did not work)

Once the Server was back I started my Media Center computer and it connected successfully. 

My Thoughts (with a disclaimer):
I really don't understand much about samba but what I think is happening ( in my case ) was some how my Samba config in my Media Center was taking control over the Server Samba config and not allowing the Server to "post"  or gain control. I welcome any talk helpful to this thought process. (even how idiotic and wrong it may be)

---

### Post by fuzzyangel on 2011-04-20
In my case, stopping the firestaster firewall was just the simple solution to have windows network accessed again!

---

### Post by ojc123 on 2011-05-01
Every 6 months I have this problem when I do the upgrade.
Every 6 months I make sure that I have installed winbind and then I do this in the terminal

sudo nano /etc/nsswitch.conf

There's a line something like this

                                 hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 

I change it to 
     
hosts:          files wins mdns4_minimal [NOTFOUND=return] dns mdns4 

I then save the file and reboot. The wins has got to come first or it doesn't work.

I don't really have a clue what this does but it seems to work.  I found it somewhere on the net and just thought I'd share.
It's just worked with 11.04 Studio.

---

### Post by capscrew on 2011-05-01
> **ojc123 said:**
> Every 6 months I have this problem when I do the upgrade.
Every 6 months I make sure that I have installed winbind and then I do this in the terminal

...


I don't really have a clue what this does but it seems to work.  I found it somewhere on the net and just thought I'd share.
It's just worked with 11.04 Studio.

The root cause of your problem is a misconfiguration of LAN side *[COLOR="Blue"]nameservices [/COLOR]* (i.e DNS (hosts)).  Winbind is not needed for the typical workgroup Samba installation.  The daemon *[COLOR="Blue"]nmbd[/COLOR]* converts DNS names to netbios names.

I originally installed Samba on Ubuntu 6.06 (Edgy).  The system is now 10.04 and the same config file (smb.conf) is used.  There is no need to modify nsswitch.conf.

---

### Post by ojc123 on 2011-05-02
> **capscrew said:**
> The root cause of your problem is a misconfiguration of LAN side *[COLOR=Blue]nameservices [/COLOR]* (i.e DNS (hosts)).  Winbind is not needed for the typical workgroup Samba installation.  The daemon *[COLOR=Blue]nmbd[/COLOR]* converts DNS names to netbios names..

Thanks but I don't understand this at all. 
Remember I said "I don't really have a clue what this does but it seems to work.  I found it somewhere on the net and just thought I'd share."
What should I do about the root cause of my problem? Please keep it as simple as possible.

---

### Post by capscrew on 2011-05-02
> **ojc123 said:**
> Thanks but I don't understand this at all. 
Remember I said "I don't really have a clue what this does but it seems to work.  I found it somewhere on the net and just thought I'd share."
What should I do about the root cause of my problem? Please keep it as simple as possible.
I don't think that it's very productive to "just share" information that you do not understand and that ultimately does not serve your fellow users.  The information is misleading and in the end creates more problems than it cures.

I'm not sure how to be more clear about how to fix your problem short of holding your hand each and every step of the way.  That is not something I am prepared to do.  As I said before you should have name services correctly configured on you LAN.  If this is done then you should be able to ping each host on you LAN by hostname.  For example I have 2 hosts named *lemon *and *orange*.  I can ping one from the other like this ```
me@orange$ ping lemon
or
me@lemon$ ping orange 
```

The most basic way is to configure the /etc/hosts file on both  hosts to contain (for example)```
192.168.x.y  orange
192.168.x.z  lemon
```

This maps the hostname to the IP address or each host.  This is the very beginnings of DNS which also maps hostnames to IP addresses.

You could (and it would be preferable ) configure the LAN side DNS in your router to perform the IP to hostname mapping.

Once this is done Samba needs no extra configuration from the way it originally was installed.  The only configuration needed is for creating shares or altering the security settings.

The key is either DNS or netbios naming services.  If you wish to use netbios directly you can follow [**_[COLOR="DarkSlateGray"]this[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10757622&postcount=20")

---

### Post by ojc123 on 2011-05-03
OK thanks.  I'm able to start researching and thinking with the information from the last post.  I'll give it a try.

---

### Post by kalyp on 2011-06-10
> **capscrew said:**
> I don't think that it's very productive to "just share" information that you do not understand and that ultimately does not serve your fellow users.  The information is misleading and in the end creates more problems than it cures.

I'm sorry, I don't agree with that. This trick solved a problem for me (cf [this thread]("http://ubuntuforums.org/showthread.php?p=10925066#post10925066")) and winbind is also recommended in the best samba tutorial I've found ([here]("http://ubuntuforums.org/showthread.php?t=288534"), even though the "wins" is in a different place).
Plus there's a lot of cases where you cannot "configure the LAN side DNS in your router to perform the IP to hostname mapping" - I don't have access to the router (my landlords), nor to the host I'm trying to reach (not my computer).

In general I feel like anytime I have a problem, I look around for any kind of trick to solve it. It it works, great, if it doesn't, I undo it. So I'm happy when people share even if they don't understand why it worked. Thanks ojc123...

---

### Post by nilbus on 2011-06-26
> **dmizer said:**
> The "Failed to retrieve share list from server" error is almost always firewall related. Try installing GUFW (via Synaptic Package Manager) and disabling the firewall in System > Administration > Firewall configuration.

Also, check Windows to make sure that no anti-virus or firewall is interfering on that end either.

This was my problem. Windows firewall was on. It said it had an exception for file sharing, but apparently it still wasn't letting things through.

---

### Post by dodjob on 2011-07-27
Hi there :)
For me, on a fresh natty install, the Netbios Name Service Request(libnet-nbname-perl)package was missing. After installing this package everything worked flawlessly :KS
Hope it helps :)
Gruß,
H.

---

### Post by redmk2 on 2011-07-27
> **dodjob said:**
> Hi there :)
For me, on a fresh natty install, the Netbios Name Service Request(libnet-nbname-perl)package was missing. After installing this package everything worked flawlessly :KS
Hope it helps :)
Gruß,
H.

Interesting.  The package you refer to is for perl scripts that explicitly call the Net::NBName and the Net::Netmask Perl modules.  What caused you to install the package?  Where did you hear of these?

What do you mean by "everything worked flawlessly"?  What did you do to configure Samba?

---

### Post by dodjob on 2011-07-27
Hi,
I'm a totaaaal n00b :) I have install this packet because when I searched for "netbios" in my "ubuntu software center" this was the first answer I got.
Yeah I know that's not very helpful but it really has worked for me and all the other things written on this thread didn't.
I didn't make any other modification at this stage on the samba config. It's an absolutely fresh install with nothing more than what Ubuntu has choose for me.
As soon as I restarted my computer I could reach my workgroup and so all the other computers on my network. I was getting a message "could not mount" and my computer was invisible from the other computers on the intranet. 
I've repeat the same operation today on another computer and it worked exactly the same way :)

---

### Post by redmk2 on 2011-07-27
> **dodjob said:**
> Hi,
I'm a totaaaal n00b :) I have install this packet because when I searched for "netbios" in my "ubuntu software center" this was the first answer I got.
Yeah I know that's not very helpful but it really has worked for me and all the other things written on this thread didn't.
I didn't make any other modification at this stage on the samba config. It's an absolutely fresh install with nothing more than what Ubuntu has choose for me.
As soon as I restarted my computer I could reach my workgroup and so all the other computers on my network. I was getting a message "could not mount" and my computer was invisible from the other computers on the intranet. 
I've repeat the same operation today on another computer and it worked exactly the same way :)

You had to do something.  The shares don't just magically invent themselves.  How did you create the shares on Ubuntu?  Could it be that you don't have any shares on the Ubuntu host?  In that case you really don't need a Samba server.  The client to view shares on other machines comes ready to use by default.

---

### Post by dodjob on 2011-07-28
> **redmk2 said:**
> You had to do something.  The shares don't just magically invent themselves.  How did you create the shares on Ubuntu?  Could it be that you don't have any shares on the Ubuntu host?  In that case you really don't need a Samba server.  The client to view shares on other machines comes ready to use by default.
lol yeah and just before this I have started my computer ;)
Ok I have mounted a new computer and install ubuntu natty on it. This computer wasn't able to reach my Intranet threw the "normal" network menu in nautilus. I have about 6 machines on this Intranet which have some shared folders.It wasn't also see-able from any other computers but pingable. When I tried to connect to other computer I got the famous "unable to mount" message. And after the install of the previously cited packet I could reach the worgkgroup /shared folders on the other machines and be seen from the other computers :)
Creating a share for me is right clicking on the folder and select the option "share" / allow guest. and that's all.Hope I've explained it ok ^^
Gruß,
H.

---

### Post by redmk2 on 2011-07-28
> **dodjob said:**
> lol yeah and just before this I have started my computer ;)
Ok I have mounted a new computer and install ubuntu natty on it. This computer wasn't able to reach my Intranet threw the "normal" network menu in nautilus. I have about 6 machines on this Intranet which have some shared folders.It wasn't also see-able from any other computers but pingable. When I tried to connect to other computer I got the famous "unable to mount" message. And after the install of the previously cited packet I could reach the worgkgroup /shared folders on the other machines and be seen from the other computers :)
Creating a share for me is right clicking on the folder and select the option "share" / allow guest. and that's all.Hope I've explained it ok ^^
Gruß,
H.

Thanks for answering.  By default, when I install 11.04 I can browse the available shares without adding any additional packages.  I'm not sure how the package helped your situation.  Interesting information for perl coders though.

---

### Post by thetopcat2010 on 2011-09-24
Hi there I am new to networking with unbuntu as i am a or was a windows user and wish to move over to unbuntu.

I have an ESXI server with Unbuntu server running on it, I have samba set up on it and can see the shares from my windows laptop.  

The problem is my desktop has unbuntu installed and I am unable to access the work group I get "Unable to mount location failed to retrieve share list from serve" can some one please help .

Many thanks
IAN (UK)

---

### Post by charrell on 2011-11-07
> **macromike said:**
> I'm not sure if this will help, but I was having the same problem and it turned out that the firewall in ubuntu was blocking the netbios ports (TCP port 139) needed to make name resolution work properly when browsing the windows network.

I solved it by installing & running gufw (gui for uncomplicated firewall) and going to the Preconfigured tab to tell it to allow the netbios-ssn service and the nfs service.

Thank you so much for this information. I have three Ubuntu servers running and I screwed up my connection to all of them. I used your information and fix the problem. I ran gufw and Incoming was set to Deny. When I changed it to Allow, everything worked fine:)

---

### Post by stevenlake on 2012-02-08
> **EvilSmith said:**
> [SIZE=2]I think I got it working guys...  This worked for me to browse my windows based machines with Ubuntu (Debian)

Here is what I did:

1.  Edited the smb.conf using    sudo gedit /etc/samba/smb.conf

          workgroup = yourworkgroupname
          server string = %h
          netbios name = computername
          wins support = yes
          ;   wins server = w.x.y.z 
          dns proxy = no
          ;   name resolve order = lmhosts wins bcast host (notice the "host" is last)
#### Networking ####

;   interfaces = 127.0.0.0/8 eth0

;   bind interfaces only = yes
####### Authentication #######

   security = SHARE (changed this from user to share)
   encrypt passwords = no


Save the file

2.  Edited the nsswitch.conf using      sudo gedit /etc/nsswitch.conf
     
        find this line 
         
              hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

        and change it to
         
              hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

Save the file

3. Install winbind

sudo apt-get install winbind

REBOOT YOUR MACHINE

AND YOU'RE DONE !!!

Oh yeah...  Previously b4 this problem was occuring I installed apache bc i wasn't able to share files with Nautilus and 
don't know if it changes samba's behavior in any way but I'm sure everybody has it installed anyway. 

You might have to wait till Nautilus scans the network to show all the machines on your network but as soon as you see them they are browsable with no delay :)
This worked for me and I hope it does for you guys[/SIZE]

Finally this solution works for me.
Thank you.

---

### Post by picbits on 2012-02-08
I've installed a few more Ubuntu machines on my network and have had the same issue as before with all of them (I posted earlier in this thread).

My findings ? My solution ?

edited smb.conf :
made the changes on the name resolve order line
changed the workgroups name to my workgroup name

edited the nsswitch
made the changes to the hosts line

Rebooted - job done.

Works every single time without fail on my system.

---

### Post by quatoria on 2012-04-08
I have tried every single thing on this forum, rebooted my machine around 50 times, installed and updated every piece of software from perl addons to winbind.

And I have done this in Linux Mint 12, Ubuntu 9.04, 10.04, 10.10, 11.04 and 11.10 (some 32bit and some 64bit). Now considering I absolutely detest the new look ubuntu and versions 11 onwards I have ignored and stayed with 10.10 it shows you how desparate I am to actually get this to work now. I cannot understand or fathom the changes with the launcher and how anyone can see them as useful. (I don't use this machine for media, I don't use it for photos, so why do I have to have the same two icons ALL THE TIME. And why can not get rid of it?) I digress.

Nothing has worked, my smb.conf is a mess with all the comments and addons, however each time it has started with a clean fresh install.

It has taken me over three days to do it.

It isn't a network issue as I have worked in IT for 14 years, I am a qualified windows engineer and my home network is set with a windows 7 ultimate, a windows 7 professional, a windows home server 2012, a ubuntu 10 machine, a ubuntu 11.04 machine (my father in law stupidly upgraded and has had graphics settings issues since) a windows XP Pro laptop and an Android 4 laptop and this one, a brand new fit-pc3 ubuntu 11.10 all of which live behind a netgear router and that has fixed and none fixed IP addresses for the network. It is this machine which won't connect to samba share (but does all the DHCP and network connections to get me on the internet.)

I can only assume since 8.04 that something seriously wrong has happened in the bowels of the install and that Ubuntu has lost it's way or simply isn't getting the grief enough to change. Leaving it to helpers on here which from the sounds of it are happily sorting it out for some but not for most.

As it happens on other flavours of linux I can only assume samba is to blame. My 10.10 machine was doing the same thing until I fixed it with I think half the options in this thread.

I hate windows as I deal with it every day but even paying windows tax and getting the AV issue every day is preferable then at least I can copy the files from my old machine and use this one to look at the media libraries or work files that I need.

Does anyone that actually works at ubuntu read these forums? 15 pages of people unhappy with a basic fundamental function of networks that came with windows 95. 17 years and the latest versions of ubuntu lack even the first generation functionality of talking to other machines on a network that is inside the same building?

---

### Post by Morbius1 on 2012-04-08
Deleted by me! Didn't realize this was from 2009/

---

### Post by bab1 on 2012-04-08
> **quatoria said:**
> I have tried every single thing on this forum, rebooted my machine around 50 times, installed and updated every piece of software from perl addons to winbind.

And I have done this in Linux Mint 12, Ubuntu 9.04, 10.04, 10.10, 11.04 and 11.10 (some 32bit and some 64bit). Now considering I absolutely detest the new look ubuntu and versions 11 onwards I have ignored and stayed with 10.10 it shows you how desparate I am to actually get this to work now. I cannot understand or fathom the changes with the launcher and how anyone can see them as useful. (I don't use this machine for media, I don't use it for photos, so why do I have to have the same two icons ALL THE TIME. And why can not get rid of it?) I digress.

Nothing has worked, my smb.conf is a mess with all the comments and addons, however each time it has started with a clean fresh install.

It has taken me over three days to do it.

It isn't a network issue as I have worked in IT for 14 years, I am a qualified windows engineer and my home network is set with a windows 7 ultimate, a windows 7 professional, a windows home server 2012, a ubuntu 10 machine, a ubuntu 11.04 machine (my father in law stupidly upgraded and has had graphics settings issues since) a windows XP Pro laptop and an Android 4 laptop and this one, a brand new fit-pc3 ubuntu 11.10 all of which live behind a netgear router and that has fixed and none fixed IP addresses for the network. It is this machine which won't connect to samba share (but does all the DHCP and network connections to get me on the internet.)

I can only assume since 8.04 that something seriously wrong has happened in the bowels of the install and that Ubuntu has lost it's way or simply isn't getting the grief enough to change. Leaving it to helpers on here which from the sounds of it are happily sorting it out for some but not for most.

As it happens on other flavours of linux I can only assume samba is to blame. My 10.10 machine was doing the same thing until I fixed it with I think half the options in this thread.

I hate windows as I deal with it every day but even paying windows tax and getting the AV issue every day is preferable then at least I can copy the files from my old machine and use this one to look at the media libraries or work files that I need.

Does anyone that actually works at ubuntu read these forums? 15 pages of people unhappy with a basic fundamental function of networks that came with windows 95. 17 years and the latest versions of ubuntu lack even the first generation functionality of talking to other machines on a network that is inside the same building?

I don't normally answer this thread as it has multiple years of misinformation and disregard for the changes that have been made to both Linux itself and Ubuntu in particular.

I'll comment on a couple of your issues though.

As to you question about Ubuntu and this forum.  This forum is not run by or managed by Canonical (Ubuntu).  If there are Canonical employees on this forum it is on there off time and not as a function of their work duties.  Ubuntu developers don't hang out here.

I have had Samba running for the last 6 years with no connection problems.  I can browse shares and manipulate files and folders with Linux and  Windows XP, Vista and 7.  I have no problems with Apple OSX and IOS (iPhone) either.

I don't believe your problem is a lack of functionality by Linux/Ubuntu or Samba, rather a lack of insight on your part as to how configure Windows and Ubuntu/Samba to interact.

If you want to start your own thread, I'll be happy to assist, but it will come with no Windows, Linux, Ubuntu or Samba bashing.  I'll be look for your post.  :-)

---

### Post by oldfred on 2012-04-08
Thread closed. 

If you have similar issues start a new thread as this is getting old & dated. Much is not current.

---

