---
title: "Wireless printing with SAMBA and CUPS"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by zcacogp on 2013-01-27
Hello, 

I am struggling to make wireless printing work with my network and machines. The setup I have is a desktop machine with a Samsung printer attached by USB cable, and which runs cups (1.6.1). The desktop machine is running 12.10 64-bit with Gnome. This works fine most of the time - I can usually print things correctly (occasionally if you print something you are told that the item has printed but it hasn't. I am hoping this isn't relevant.) 

This desktop machine shares the printer via SAMBA, and I have attached the smb.conf file at the end of this post. All the machines are on the same workgroup, and smbtree gives this: 

```

ogp@desktop:~$ smbtree
Enter ogp's password: 
DGCNET
	\\X61S           		x61s server (Samba, Ubuntu)
		\\X61S\Samsung-ML-2240	Samsung ML-2240
		\\X61S\print$         	Printer Drivers
		\\X61S\IPC$           	IPC Service (x61s server (Samba, Ubuntu))
	\\DESKTOP        		desktop server (Samba, Ubuntu)
		\\DESKTOP\ML-2240-Series 	Samsung ML-2240 Series
		\\DESKTOP\IPC$           	IPC Service (desktop server (Samba, Ubuntu))
		\\DESKTOP\Pharmacy       	Pharmacy shared drive (NTFS)
		\\DESKTOP\Ianthe         	Ianthe shared drive (EXT3)
		\\DESKTOP\Helena         	Helena shared drive (EXT3)
		\\DESKTOP\cdrom          	Samba server's CD-ROM
		\\DESKTOP\print$         	Printer Drivers
	\\DELL           		dell server (Samba, Ubuntu)
		\\DELL\Samsung-ML-2240	Samsung ML-2240
		\\DELL\print$         	Printer Drivers
		\\DELL\IPC$           	IPC Service (dell server (Samba, Ubuntu))
ogp@desktop:~$ 

```

You can see the desktop machine ('desktop') and the two laptops ('dell' and 'X61S').

I have some laptop machines, all of which run 12.10 32-bit with Gnome, and all of which have cups 1.6.1 installed as well. You can see the samsung printer across the network from these machines fine, but printing from them is a bit more hit-and-miss. Occasionally it works fine, but often you can try and print an item and it claims to print but doesn't. 

There doesn't seem to be any logic in what causes it to print or not; I have tried restarting SAMBA on the server and rebooting the client and server machines, and none of these seem to make much difference. Everything else across SAMBA (three file shares) works 100% reliably. 

(I did have a problem with the client machines failing to authenticate for the printer, but this was solved by adding the line "use client driver = yes" to the smb.conf file on the server, as outlined here: [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/990388](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/990388) ) 

I am confused as to why there is flaky behaviour - why it sometimes works but sometimes doesn't. I am also confused as to whether the client machines use the cups that are installed on them, or whether they connect directly via SAMBA to the cups on the server (i.e. I don't fully understand how SAMBA and cups work together.) As a result of this, I am not 100% sure which set of error logs I should be looking in to find information about these missing printer jobs - whether to look on the clients or server. The behaviour is consistent across all clients so I suspect the problem is with the server, and I have attached /var/log/cups/error_log to this post as well, although it doesn't have anything in it that looks helpful to me. 

If anyone can shed any light on this problem I'd be grateful - thank you. 


Oli. 

/var/log/cups/error_log:
```

E [27/Jan/2013:20:39:12 +0000] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
E [27/Jan/2013:20:39:13 +0000] [cups-driverd] Bad driver information file "/usr/share/cups/drv/cupsfilters.drv"!
E [27/Jan/2013:20:39:59 +0000] [cups-driverd] Bad driver information file "/usr/share/cups/drv/cupsfilters.drv"!
W [27/Jan/2013:20:40:02 +0000] AddProfile failed: org.freedesktop.DBus.Error.UnknownMethod:No such interface `org.freedesktop.ColorManager' on object at path /org/freedesktop/ColorManager/devices/cups_ML_2240_Series
E [27/Jan/2013:20:47:27 +0000] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [27/Jan/2013:20:47:27 +0000] AddProfile failed: org.freedesktop.DBus.Error.UnknownMethod:No such interface `org.freedesktop.ColorManager' on object at path /org/freedesktop/ColorManager/devices/cups_ML_2240_Series
E [27/Jan/2013:20:56:43 +0000] [cups-driverd] Bad driver information file "/usr/share/cups/drv/cupsfilters.drv"!
W [27/Jan/2013:21:08:22 +0000] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'ML-2240-Series-Gray..' already exists
W [27/Jan/2013:21:08:22 +0000] CreateDevice failed: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-ML-2240-Series' already exists

```

smb.conf (on the server): 
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
	workgroup = dgcnet

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
	security = user
	username map = /etc/samba/smbusers

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
	encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;	passdb backend = tdbsam

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
   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups

use client driver = yes

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
;	guest ok = no
;	guest account = nobody

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
   guest ok = yes
   read only = yes
   create mask = 0700



# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	browseable = yes
	writeable = yes
	guest ok = yes

# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
[cdrom]
	comment = Samba server's CD-ROM
	read only = no
	locking = no
	path = /media/dvd
	guest ok = yes

[Helena]
	comment = Helena shared drive (EXT3)
	writeable = yes
	locking = no
	path = /media/Helena
;	browseable = yes
	valid users = cmp, ogp


[Ianthe]
	comment = Ianthe shared drive (EXT3)
	writeable = yes
	locking = no
	path = /media/Ianthe
;	browseable = yes
	valid users = cmp, ogp


[Pharmacy]
	comment = Pharmacy shared drive (NTFS)
	writeable = yes
	locking = no
	path = /media/Pharmacy
;	browseable = yes
	valid users = cmp, ogp


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
#   preexec = /bin/mount /cdrom
#   postexec = /bin/umount /cdrom

```

Edited to Add: Searching this forum suggests that problems with CUPS and SAMBA are not uncommon, there are threads here: 

[http://ubuntuforums.org/showthread.php?t=2073014&highlight=samba+cups](http://ubuntuforums.org/showthread.php?t=2073014&highlight=samba+cups)
[http://ubuntuforums.org/showthread.php?t=2089946&highlight=samba+cups](http://ubuntuforums.org/showthread.php?t=2089946&highlight=samba+cups)
[http://ubuntuforums.org/showthread.php?t=2032191&highlight=samba+cups](http://ubuntuforums.org/showthread.php?t=2032191&highlight=samba+cups)

... and several more. Google tells me that there have been problems with SAMBA and CUPS since 12.04, but is there a solution?

---

### Post by zcacogp on 2013-02-22
Bit of an update on this. I have been playing around with the printing and suspect that the problem lies in the fact that the printing is intermittant from the machine the printer is plugged into - the print server. This applies no matter which machine is used as the server - the desktop computer or the laptop computer. 

The bahviour is always the same; it will print the first job reliably, but won't reliably print from then on. (Sometimes it will, after a delay of several minutes. Most of the time it won't print at all.) However if you unplug the printer from the USB port and plug it back in again then it will print reliably for the next job, or so it seems. So unplugging the printer and re-plugging it 'resets' it. 

This is as far as I can get - why would this be so? 

All help warmly welcomed - thank you. 


Oli.

---

