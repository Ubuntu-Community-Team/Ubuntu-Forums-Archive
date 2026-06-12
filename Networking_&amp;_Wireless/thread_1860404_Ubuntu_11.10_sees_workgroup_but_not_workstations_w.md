---
title: "Ubuntu 11.10 sees workgroup but not workstations within"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by Grumn on 2011-10-14
Hey guys!
I'm a total "noob" when it comes to Ubuntu, but I've been quite a fan of it for about a year and a half now. I've been promoting it to friends, family,...

I've hardly had any troubles with it, everything used to work out of the box except for 1 little issue:
Adding a Windows-printer via Samba only works half the time for me.

I've had this trouble since 10.04... When I browse the network via Samba, it finds the workgroup "WORKGROUP", but when I click on the triangle attempting to see what's deeper within the workgroup the "busy"-mouse pointer comes up. After a few seconds it disappeared resulting in nothing changing... The workgroup is still listed, but no printer.

The printer is connected to a 6-7 year old Windows XP desktop machine which serves as a small "printing server", that way my mom can print wirelessly. The problem used to resolve itself in some manner after a bit of googling and testing all the answers I've found. Last time (Ubuntu 11.04) the solution was to disable the firewall using the terminal.

After my clean install of Ubuntu 11.10 nothing seems to work.... I've tried:
[LIST]
[*]Disabling the firewall on the Ubuntu machine
[*]Disabling the firewall and internet security on the Windows XP machine
[*]Browsing the network using Nautilus, resulting in an error message when I try to open WORKGROUP: "Failed to retrieve share list from server"
[*]Renaming the workgroup to MSHOME and changing it in the smb.conf file and vice-versa
[/LIST]

No luck at all...

I'm hoping one of you more experienced Ubuntu users have ran into the same problem or know the solution...

Thanks in advance!
Grumn

---

### Post by capscrew on 2011-10-14
> **Grumn said:**
> Hey guys!
I'm a total "noob" when it comes to Ubuntu, but I've been quite a fan of it for about a year and a half now. I've been promoting it to friends, family,...

I've hardly had any troubles with it, everything used to work out of the box except for 1 little issue:
Adding a Windows-printer via Samba only works half the time for me.

I've had this trouble since 10.04... When I browse the network via Samba, it finds the workgroup "WORKGROUP", but when I click on the triangle attempting to see what's deeper within the workgroup the "busy"-mouse pointer comes up. After a few seconds it disappeared resulting in nothing changing... The workgroup is still listed, but no printer.

The printer is connected to a 6-7 year old Windows XP desktop machine which serves as a small "printing server", that way my mom can print wirelessly. The problem used to resolve itself in some manner after a bit of googling and testing all the answers I've found. Last time (Ubuntu 11.04) the solution was to disable the firewall using the terminal.

After my clean install of Ubuntu 11.10 nothing seems to work.... I've tried:
[LIST]
[*]Disabling the firewall on the Ubuntu machine
[*]Disabling the firewall and internet security on the Windows XP machine
[*]Browsing the network using Nautilus, resulting in an error message when I try to open WORKGROUP: "Failed to retrieve share list from server"
[*]Renaming the workgroup to MSHOME and changing it in the smb.conf file and vice-versa
[/LIST]

No luck at all...

I'm hoping one of you more experienced Ubuntu users have ran into the same problem or know the solution...

Thanks in advance!
Grumn

It sounds like you need to modify the smb.conf file to allow netbios broadcasts of the Ubuntu host and its printer share.

Provide the output (inside the ```
  [/ code] blocks) of[CODE]testparm -s
``` and also the output of the command```
hostname
```

---

### Post by Bill Grabowski on 2011-10-14
> **capscrew said:**
> It sounds like you need to modify the smb.conf file to allow netbios broadcasts of the Ubuntu host and its printer share.

Provide the output (inside the ```
  [/ code] blocks) of[CODE]testparm -s
``` and also the output of the command```
hostname
```

I'm having exactly the same issue, so here's my output:

```

bill@linuxantec:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Unknown parameter encountered: "enable spools"
Ignoring unknown parameter "enable spools"
Processing section "[homes]"
Processing section "[netlogon]"
Processing section "[profiles]"
Processing section "[printers]"
Processing section "[pdf-documents]"
Processing section "[pdf-printer]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
	workgroup = HOME
	netbios name = SAMBA24
	server string = Samba file and print server
	interfaces = 127.0.0.1/8, 192.168.0.0/24
	bind interfaces only = Yes
	update encrypted = Yes
	client schannel = No
	server schannel = No
	allow trusted domains = No
	obey pam restrictions = Yes
	passwd program = /usr/bin/passwd '%u'
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	passwd chat timeout = 120
	username map = /etc/samba/smbusers
	password level = 6
	username level = 6
	unix password sync = Yes
	log file = /var/log/samba/samba.log
	max log size = 1000
	name resolve order = wins lmhosts bcast
	client signing = No
	client use spnego = No
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = cups
	machine password timeout = 120
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	delete user script = /usr/sbin/userdel '%u'
	add group script = /usr/sbin/groupadd '%g'
	delete group script = /usr/sbin/groupdel '%g'
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	logon script = %G.bat
	logon path = \\%L\profiles\%u
	logon drive = m:
	logon home = \\%L\homes\%u
	os level = 33
	local master = No
	domain master = No
	dns proxy = No
	remote announce = 192.168.0.255
	remote browse sync = 192.168.0.255
	idmap uid = 16777216-33554431
	idmap gid = 16777216-33554431
	template shell = /dev/null
	winbind separator = @
	winbind cache time = 360
	winbind use default domain = Yes
	winbind trusted domains only = Yes
	winbind nested groups = No
	winbind nss info = no
	hosts allow = 127., 192.168.0.
	cups options = raw
	follow symlinks = No

[homes]
	comment = Home Directories
	path = /home
	read only = No
	locking = No
	strict locking = No

[netlogon]
	comment = Network Logon Service
	path = /home/netlogon
	read only = No
	locking = No
	strict locking = No

[profiles]
	comment = User Profiles
	path = /var/samba/profiles
	read only = No
	create mask = 0600
	directory mask = 0700
	browseable = No
	locking = No
	strict locking = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	printable = Yes
	browseable = No
	locking = No
	strict locking = No

[pdf-documents]
	comment = Converted PDF Documents
	path = /home/pdf-documents
	read only = No
	guest ok = Yes
	locking = No
	strict locking = No

[pdf-printer]
	comment = PDF Printer Service
	path = /tmp
	guest ok = Yes
	printable = Yes
	printing = bsd
	print command = /usr/bin/gadmin-samba-pdf %s %u
	lpq command = 
	use client driver = Yes

```

... and:
```

bill@linuxantec:~$ hostname
linuxantec

```

Bill

---

### Post by Grumn on 2011-10-15
> **capscrew said:**
> It sounds like you need to modify the smb.conf file to allow netbios broadcasts of the Ubuntu host and its printer share.

Provide the output (inside the ```
  [/ code] blocks) of[CODE]testparm -s
``` and also the output of the command```
hostname
```

Thanks for responding.

Here's the output when I do *testparm -s*:

```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist
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

And here's the output of *hostname*:

```

HP-DOT-SE

```

Thanks for helping,
Grumn

---

### Post by capscrew on 2011-10-15
Load smb config files from /etc/samba/smb.conf
> **Bill Grabowski said:**
> I'm having exactly the same issue, so here's my output:

...

Your problems do not seem to be the same as the OP even if the symptoms seem to be the same.  IT appears you  have installed and used *gadmin*.  I don't use that tool as it unnecessarily modifies the smb.conf file for its own ends.  I suggest you start your own thread and describe specific setup and your problems with what you have installed.  You can of course follow this thread, but it may not resolve your specific problems.

---

### Post by Grumn on 2011-10-15
> **capscrew said:**
> Load smb config files from /etc/samba/smb.conf


...

Your problems do not seem to be the same as the OP even if the symptoms seem to be the same.  IT appears you  have installed and used *gadmin*.  I don't use that tool as it unnecessarily modifies the smb.conf file for its own ends.  I suggest you start your own thread and describe specific setup and your problems with what you have installed.  You can of course follow this thread, but it may not resolve your specific problems.

I've opened the smb.conf file, these are the settings within the file:

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
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
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

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

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
;   printing = cups
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
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
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
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

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
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

```

I hope you can help me resolve my problem.

Thanks in advance,
Grumn

---

### Post by capscrew on 2011-10-15
> **Grumn said:**
> Thanks for responding.

Here's the output when I do *testparm -s*:

```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
[COLOR="Red"]
        netbios name = HP-DOT-SE
        name resolve order = bcast host[/COLOR]
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

And here's the output of *hostname*:

```

HP-DOT-SE

```

Thanks for helping,
Grumn

I suggest you explicitly declare the NETBIOS name in your /etc/samba/smb.conf file and have Samba serch via bcast for it.

To do that you have to add the following in the [global] section of your smb.conf file
```
netbios name = HP-DOT-SE
name resolve order = bcast host
```

Add them just like I have (above in red) in your post.  Then you need to restart Samba like this```

sudo service smbd restart
sudo service nmbd restart
```

Wait a few minutes for the system to absorb the changes and try browsing for the printer shares.

Let us know your results.

---

### Post by Grumn on 2011-10-15
> **capscrew said:**
> I suggest you explicitly declare the NETBIOS name in your /etc/samba/smb.conf file and have Samba serch via bcast for it.

To do that you have to add the following in the [global] section of your smb.conf file
```
netbios name = HP-DOT-SE
name resolve order = bcast host
```Add them just like I have (above in red) in your post.  Then you need to restart Samba like this```

sudo service smbd restart
sudo service nmbd restart
```Wait a few minutes for the system to absorb the changes and try browsing for the printer shares.

Let us know your results.

I edited the smb.conf file, restarted the machine (as the restart code you provided didn't work) and I can add the Windows XP printer and print.

Thanks a lot for all the help!

Greets,
Grumn

---

### Post by capscrew on 2011-10-15
> **Grumn said:**
> I edited the smb.conf file, restarted the machine (as the restart code you provided didn't work) and I can add the Windows XP printer and print.

Thanks a lot for all the help!

Greets,
Grumn

Actually I expected that.  You are only using the Samba client I expect.  But it worked out anyway and that's good.

---

### Post by Bill Grabowski on 2011-10-15
> **capscrew said:**
> Load smb config files from /etc/samba/smb.conf


...

Your problems do not seem to be the same as the OP even if the symptoms seem to be the same.  IT appears you  have installed and used *gadmin*.  I don't use that tool as it unnecessarily modifies the smb.conf file for its own ends.  I suggest you start your own thread and describe specific setup and your problems with what you have installed.  You can of course follow this thread, but it may not resolve your specific problems.

capscrew,

You are correct: I did find and use **Gadmin-Samba** and it did do some different things to the *smb.conf*, so... I added the following to the smb.conf:

```

[printers]
	comment = All Printers
	path = /var/spool/samba
	browseable = yes
	printable = yes
	locking = no
	strict locking = no
	guest ok = yes

[share]
	comment = Ubuntu File Server Share
	path = /srv/samba/share
	browesable = yes
	guest ok = yes
	create mask = 0755

```

... and *that* seems to now work. I get good networking including network printing. I also had to find and check the box next to "Show printers shared by other systems" which is buried in the **Settings...** menu item under **Server** for the **Printing** app in **System Settings...**. Whew!

Thanks for pointing the way.:popcorn:

Bill

---

### Post by robhills on 2012-03-03
Thanx Capscrew.

This worked for me under similar circumstances

:popcorn:

---

