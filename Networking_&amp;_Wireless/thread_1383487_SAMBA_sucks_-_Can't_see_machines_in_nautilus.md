---
title: "SAMBA sucks - Can't see machines in nautilus"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by dccrens on 2010-01-17
Just had an upgrade of a couple of packages the other night relating to SAMBA. now SAMBA is weirding out. I am running several ubuntu 9.10 machines along with two Buffalo linkstation NAS's and a couple of winblows boxes. I am knowledgeable with Linux, Ubuntu and computers in general as I am an SA...I had them configured via samba to share and share alike. All has been good for months (since I upgraded from 8.10 to 9.10). 

Now, after the last upgrade of the SAMBA related packages, 1 of the ubuntu 9.10 boxes can no longer see all the other boxes. From the effected box, I can see a couple of the the other ubuntu boxes but not the NAS and not a couple of other boxes. It is really strange. All the other ubuntu boxes are still working fine and can see and browse all the other machine/shares on the network... 

I have checked smb.conf, hosts, nsswitch.conf and everything else I can think of that might have an effect. All of the files smb.conf, etc are configured the same from machine to machine. Winbind is installed. I have re-followed/re-read many of the guides on SAMBA with no luck.  

The real weird thing is, that in nautilus, I can actually type in the address of a machine or NAS like "smb://caverstor/media/" and it displays fine. So samba is actually working. However, when I open "network" from the "places" menu in nautilus, rather than seeing all the machines and NAS boxes in the top level or under "Windows Network" and under the workgroup which is in my case "5513-CCAIT", only two of the machines show up. I have removed all samba related packages and reinstalled with the same results. I have checked everything I can think of. 

The other "oddity" is that if I stop and restart the samba daemon, and then open a nautilus browser, it will work - all the machines will be there - but only once!!! If I close the nautilus window and then reopen they will be gone!! 

Any help is appreciated. 

Anyone with any thoughts on what else to check?

I have changed the name resolve order - trying several differnt ways with no change. 

I have tried it with the netbios name and without

testparm shows no errors

I can ping all machines both ways

nslookup works

my smb.conf looks like this:

```

#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = 5513-ccait
	netbios name = cavermax-ubuntu
# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
;	dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
name resolve order = lmhosts wins bcast host

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
	syslog only = yes

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
;	syslog = 1

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
;	guest ok = no
;	guest account = nobody

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

[samba]
	path = /home/samba
	writeable = yes
;	browseable = yes
	guest ok = yes

[Software]
	comment = Linux Software
	path = /home/dccrens/Software
	writeable = yes
;	browseable = yes
	valid users = dccrens

[USB_L]
	path = /media/USB_L
	writeable = yes
;	browseable = yes
	guest ok = yes

[Downloads]
	comment = Drive E Downloads
	path = /media/E/Downloads
	writeable = yes
;	browseable = yes
	valid users = dccrens

[To Dvd]
	comment = Drive E To DvD
	path = /media/E/To Dvd
	writeable = yes
;	browseable = yes
	valid users = dccrens

[NetWork Data]
	comment = Drive F Network Data
	path = /media/F/NetWork Data
	writeable = yes
;	browseable = yes
	guest ok = yes

[Finance]
	comment = Finacials
	path = /media/E/Data/Finance
	writeable = yes
;	browseable = yes
	guest ok = yes

[dccrens Documents]
	comment = All Documents
	path = /media/E/Data/dccrens Documents
	writeable = yes
;	browseable = yes
	guest ok = yes

[addata]
	path = /home/dccrens/addata
	writeable = yes
;	browseable = yes
	valid users = dccrens

```


and my nsswitch.conf looks like this

```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.
# hosts:          files dns wins mdns4_minimal [NOTFOUND=return] mdns4


passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

the output of testparm is:

```
 
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[samba]"
Processing section "[Software]"
Processing section "[USB_L]"
Processing section "[Downloads]"
Processing section "[To Dvd]"
Processing section "[NetWork Data]"
Processing section "[Finance]"
Processing section "[dccrens Documents]"
Processing section "[addata]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = 5513-CCAIT
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog only = Yes
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = lmhosts wins bcast host
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

[samba]
	path = /home/samba
	read only = No
	guest ok = Yes

[Software]
	comment = Linux Software
	path = /home/dccrens/Software
	valid users = dccrens
	read only = No

[USB_L]
	path = /media/USB_L
	read only = No
	guest ok = Yes

[Downloads]
	comment = Drive E Downloads
	path = /media/E/Downloads
	valid users = dccrens
	read only = No

[To Dvd]
	comment = Drive E To DvD
	path = /media/E/To Dvd
	valid users = dccrens
	read only = No

[NetWork Data]
	comment = Drive F Network Data
	path = /media/F/NetWork Data
	read only = No
	guest ok = Yes

[Finance]
	comment = Finacials
	path = /media/E/Data/Finance
	read only = No
	guest ok = Yes

[dccrens Documents]
	comment = All Documents
	path = /media/E/Data/dccrens Documents
	read only = No
	guest ok = Yes

[addata]
	path = /home/dccrens/addata
	valid users = dccrens
	read only = No

```

This is truely maddening.... :confused:

Thanks for the help...
Dave

---

### Post by dccrens on 2010-01-31
{{{BUMP}}}

Anyone? I would really like to get this working. I have read hundreds of threads and tried many configs. No luck.

---

### Post by dccrens on 2010-01-31
Is it possible this is a Nautilus bug? Since I can browse shares by putting in the full path and from the CLI that means SAMBA is working... Just can see the machines under the workgroup or network in Nautilus...

---

### Post by pdc on 2010-01-31
swerdna is very good on samba but does not always have time to follow the forums

[http://ubuntu.swerdna.org/](http://ubuntu.swerdna.org/)

he seems happy for you to email him; (when he is not throwing a prawn on the BBQ in Brisbane ...)

let us know if you can get it fixed

---

### Post by dccrens on 2010-01-31
Yeee ha!

I just spent a couple hours reading swerdna's site. Killer site! Great info all around. 

After going though his SAMBA pages and reconfiguring all of my machines - everything now works. I believe I was having problems with the LMB and WINS.

After configuing only one machine as the LMB and WINS and then configuring the rest as clients, all is good...

> **pdc said:**
> swerdna is very good on samba but does not always have time to follow the forums

[http://ubuntu.swerdna.org/](http://ubuntu.swerdna.org/)

he seems happy for you to email him; (when he is not throwing a prawn on the BBQ in Brisbane ...)

let us know if you can get it fixed

---

### Post by pdc on 2010-01-31
well done; great work; flick him an email if you get a sec; I am sure he will be pleased to hear of your success

---

