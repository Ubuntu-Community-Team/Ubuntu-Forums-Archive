---
title: "Cannot copy to shared drive"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by adzik on 2009-05-26
I have an interesting issue with a samba share on my network.
This particular laptop is using hardy/8.04.
I have installed samba etc. to make use of this share properly, and somewhere along the way, the connection became a one way street.
I can view and list everything within the share, so it is ultimately working, but I can only send files to the path, not copy over or receive from. Basically, when I attempt to copy a file or folder over to the laptop, it fails, but copying to the share is just fine. 
I'm a bit stuck here. Any help or direction appreciated.

---

### Post by adzik on 2009-05-27
Any takers?

---

### Post by swerdna on 2009-05-27
> **adzik said:**
> I have an interesting issue with a samba share on my network.
This particular laptop is using hardy/8.04.
I have installed samba etc. to make use of this share properly, and somewhere along the way, the connection became a one way street.
I can view and list everything within the share, so it is ultimately working, but I can only send files to the path, not copy over or receive from. Basically, when I attempt to copy a file or folder over to the laptop, it fails, but copying to the share is just fine. 
I'm a bit stuck here. Any help or direction appreciated.

It's not clear enough for me, excuse my poor language skills. You have a laptop with a Samba share and some second computer.
A couple of questions to make it absolutely clear what the problem is:
[LIST=1]
[*]What operating system is running on the second computer?
[*]When you sit at the laptop can you copy a file to the laptop from the second computer?
[*]When you sit at the laptop can you copy a file to the second computer from the laptop?
[*]When you sit at the second computer can you copy a file to the laptop from the second computer?
[*]When you sit at the second computer can you copy a file to the second computer from the laptop?
[/LIST]

---

### Post by adzik on 2009-05-27
Okay, to clarify, the shared drive on the network is a NAS drive (not a pc), running a fat32. That's all it supports. So really, there is no 'second' computer involved. I do have another laptop that accesses this network drive, but it doesn't have the same problem and works fine. It's running ubuntu 9.04.
The laptop with the problem has ubuntu 8.04 (cannot upgrade for various reasons) and will only view and copy files/folder to the network share/drive, but cannot copy anything back to the laptop. 
It also is unable to copy anything from the other 9.04 laptop, only send files to it. 
Therefore:
[LIST]
laptop 8.04 can't receive from nas drive or other laptop, but can view and send files/folders
[/LIST]
[LIST]laptop 9.04 can copy and send to the nas drive and laptop 8.04 correctly
[/LIST]

Hope that helps.

---

### Post by swerdna on 2009-05-27
That's a really strange situation. I haven't come across a block like it before. Puzzled. Try these diagnostic exercises so we can get a better idea of what's happening:

[LIST=1]
[*]I imagine you are using nautilus as a GUI browser in 8.04. What version of Nautilus is installed?
[*]What permissions and ownership do you see when you browse the files in Nautilus? For example here are the browse permissions results for an item when I view it over the network:> filename size date -rw-r--r-- john usersWhat do you see in your file browser?
[*]If you have a NAS with servername "nas_server" and a share called "nas_share" and no password required, you can connect in a Gnome terminal window with:```
smbclient //nas_server/nas_share -N 
```Then you can list the contents with this command at the smb> prompt:```
ls
```Then try to copy a file with this command at the smb> prompt:```
get filename
```Do those commands allow you to list and retrieve files?
[/LIST]

---

### Post by adzik on 2009-05-28
The nautilus version is 2.22.5.1

When viewing files over the network, it tells me that "permissions could not be determined", but I can see all the files and folders in nautilus just fine.

I tried connecting to the share from the terminal and it reads:
```
smb: \> Read from server failed, maybe it closed the connection
```
It keeps repeating this message non-stop every few seconds. 
I can mount and unmount it correctly through nautilus though.

Needless to say, I can't check anything else through the terminal since it won't successfully connect that way. :-k

---

### Post by swerdna on 2009-05-29
The bug was in Nautilus 2.22.2. I don't know if the bug persisted into your version (2.22.5). Certainly it's gone by the time of my current version (2.24.1). Here's a report on the bug from openSUSE (but it was found in all Nautilii of the time): [https://bugzilla.novell.com/show_bug.cgi?id=401238](https://bugzilla.novell.com/show_bug.cgi?id=401238)

I mention the bug for completeness, in case other readers of this thread think they have that problem too, but I see that bug as not the issue here because the issue persists from the command line using smbclient.

What can I say? Not a lot. I'm completely puzzled. I see on this link:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/226777](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/226777)
the suggestion that it's hardware related. But I don't fully understand that link.

My intuition based on experience tells me it's likely machine based mixed with the software. By this I mean it's probable that that your operating system on a different computer wouldn't reproduce the problem. I don't think it's the software. But who can validate or invalidate that -- only you I think.

I do hope someone more experienced comes along with a fresh idea.

Good luck.

---

### Post by Jive Turkey on 2009-05-29
On the server computer run the command "testparm" and post the second part of the output where it shows the info about the shares and thier permissions.  Make sure your user has both read and write permissions.  It may be possible to only have write and view permissions.

check that the two computers allow communications (at least with each other) on ports 445 and 139 also.

---

### Post by swerdna on 2009-05-29
> **Jive Turkey said:**
> On the server computer run the command "testparm" and post the second part of the output where it shows the info about the shares and thier permissions.  Make sure your user has both read and write permissions.  It may be possible to only have write and view permissions.

check that the two computers allow communications (at least with each other) on ports 445 and 139 also.

I see two difficulties with that advice:
[LIST=1]
[*]adzik cannot run testparm because it's a NAS drive
[*]The share on the NAS has read permissions enabled for the OP's second laptop so the read-block originates in the problematic laptop only.
[/LIST]
But the port investigation is a good idea. I've never properly understood the ports functionality, can you tell me why it's only necessary to check the TCP ports and not the UDP ports in this case? Thanks.

@adzik, can you post you samba config file (smb.conf) it should be checked just in case.

---

### Post by adzik on 2009-05-29
Is there another possible solution that is safe to perform?
For instance, restarting the networking components from scratch or something? If not, I should probably start looking at a reinstall of a more functional system, which I would still prefer to avoid.
I'll read through those bug reports to see if I can pick up some clues.

Here is my smb.conf```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = workgroup

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;	wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
	dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#THE LANMAN FIX
;	client lanman auth = yes
;	client ntlmv2 auth = no

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
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
	log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
	max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;	syslog only = no

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
	security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;	encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
	passdb backend = tdbsam

	obey pam restrictions = yes

;	guest account = nobody
	invalid users = root

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

# This option controls how nsuccessful authentication attempts are mapped 
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
;	logon path = \\%n\%u\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;	logon home = \\%n\%u

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
;	load printers = yes

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
;	socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;	domain master = auto

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
;	guest ok = no
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

```

---

### Post by swerdna on 2009-05-29
H again.

Regarding the bug reports -- I think that will not be the problem (but hey, who knows really?). The link to the thread that talks about a hardware problem is interesting though.

That's a pretty interesting looking smb.conf. There are no shared resources in it (which is fine) so you're only using Samba to see the NAS, not as a server.

The [global] stanza looks weird. When I run testparm on it I get this response:
```
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
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
	invalid users = root
```
That's so full of strange parameter definitions that I would change it completely, to the alternate I recommend below.

First back it up with this Gnome Terminal command: ```
sudo cp /etc/samba/smb.conf /etc/samba/weird_old_smb.conf
```
Then open the original in a superuser text editor with this command:```
gksudo gedit /etc/samba/smb.conf
```
When you have it open, clean out eveything in it and paste the following recommended alternative into it:
> # This is a (non-preferred) Local Master Browser
[global]
workgroup = NAME_OF_WORKGROUP
netbios name = name_of_this_workstation
name resolve order = bcast host lmhosts wins
server string = %h server (Samba, Ubuntu)
printing = cups
printcap name = cups
printcap cache time = 750
cups options = raw
load printers = yes
use client driver = yes
map to guest = Bad User
local master = yes
os level = 33
usershare allow guests = Yes
usershare max shares = 100
usershare owner only = False

[printers]
comment = All Printers
path = /var/spool/samba
printable = Yes
create mask = 0700
browseable = No
guest ok = Yes

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
Note you must change NAME_OF_WORKGROUP to the workgroup defined in the NAS configuration. Also, replace name_of_this_workstation to something appropriate, like lappy804.

[PS if you don't know the workgroup name, run this console command: ```
sudo smbtree -N
``` and it will be in the results]

Then save and exit. Then reboot to restart the Samba daemons and set an election for master browser in train. Then try again.

That's all I can think of that would come under "another possible solution that is safe to perform".

Reference: [SOHO LAN Primer]("http://www.swerdna.net.au/linhowtolanprimer.html")

---

### Post by Jive Turkey on 2009-05-29
> **swerdna said:**
> I see two difficulties with that advice:
[LIST=1]
[*]adzik cannot run testparm because it's a NAS drive
[*]The share on the NAS has read permissions enabled for the OP's second laptop so the read-block originates in the problematic laptop only.
[/LIST]
But the port investigation is a good idea. I've never properly understood the ports functionality, can you tell me why it's only necessary to check the TCP ports and not the UDP ports in this case? Thanks.

@adzik, can you post you samba config file (smb.conf) it should be checked just in case.

My mistake, I thought it was an ubuntu box running samba-server, and I presumed ssh to run testparm. I'll reread the thread and see if I can come up with anything else.

You are right about the ports too,
137, 138 use udp
139, 445 use tcp
I'm not certain why but the global section in my samba server only specifies 139 and 445, and it works.  If the problematic laptop has any of them closed that *might* be the problem.  I've never used a NAS unit so I don't think I can be much help.

---

### Post by adzik on 2009-05-29
Thanks for the help here. I will test it all out tonight and report back. And I think I will rename my smb.conf to what you suggested:  weird_old_smb.conf.  Love it! :D

---

### Post by swerdna on 2009-05-29
> **Jive Turkey said:**
> My mistake, I thought it was an ubuntu box running samba-server, and I presumed ssh to run testparm. I'll reread the thread and see if I can come up with anything else.

You are right about the ports too,
137, 138 use udp
139, 445 use tcp
I'm not certain why but the global section in my samba server only specifies 139 and 445, and it works.  If the problematic laptop has any of them closed that *might* be the problem.  I've never used a NAS unit so I don't think I can be much help.
Thanks for that Jive Turkey. Adzik has no specification for ports. That will default to "smb ports = 445 139". So it's not necessary to bother with including the parameter definition for ports unless you want to deviate from the default.

---

### Post by adzik on 2009-05-29
Alright, I went through the steps, and rebooted.
Also checked the settings on the nas just in case.
I went through some of the initial steps in this thread upon reboot, and I still receive the same errors, and the main issue is unchange. Still no dice.
I will read over the primer on your site to get more familiar with this in general.
Any other ideas?

---

### Post by swerdna on 2009-05-29
> **adzik said:**
> Alright, I went through the steps, and rebooted.
Also checked the settings on the nas just in case.
I went through some of the initial steps in this thread upon reboot, and I still receive the same errors, and the main issue is unchange. Still no dice.
I will read over the primer on your site to get more familiar with this in general.
Any other ideas?
It's clear that it's not the setup at the level of smb.conf. And I assume there are no firewalls to muddy the waters. So It comes down to the underlying software being corrupted or the hardware being broken. At those levels I have no brilliant Ideas. If you have another network card, you could try swapping it to that for a test. Also,don't forget that average routers and other network devices need to be switched off and on from time to time.

---

### Post by adzik on 2009-05-29
Has hardy (8.04) been known to have any issues with networking? I find this strange because running a mepis livecd allowed me to access the nas properly. I guess this mean a reinstall after all. I'll have to see what the best course of action is here.

Thanks for all your help. Appreciate it a lot.

---

