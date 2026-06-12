---
title: "who's good with samba?"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-04-13
Got a question here that I think is relatively simple, but I just don't understand.

I set up several samba users for backup purposes, but I also have a guest user because friends often bring their laptops over and want to pass off pictures to me from a recent trip, so I'll just tell them to log into my server from their XP or Vista laptop (most commonly) and log in as guest and kick the pictures over. Then I'll sort them accordingly.

All of the users EXCEPT "Guest" are part of the Sambashare group.

The octal rights to the samba network folder are 775. So the owner + group has full reign while everyone else can simply access.

This is where I get confused. I created a folder by a user within sambashare. It came through as jason:sambashare, as far as ownership goes.

Then I logged into the samba from an XP laptop. I logged in as guest, which is NOT part of the sambashare account.

From the XP laptop, I was able to rename, delete, modify, do anything I wanted to this folder.

I can see this working out this way if guest had been part of the sambashare, because then guest has full access over it. But how does guest have this right? Do octal rights only apply to local permissions? When Samba is in the picture, as long as I have readable/writable as valid on the folder, can ANY user who authenticates properly to the folder have full access over the files?

---

### Post by dmizer on 2009-04-13
Well, first of all "guest" doesn't mean "guest account". It merely means that samba doesn't prompt for a password (open share).

Please post your /etc/samba/smb.conf file.

Your solution will probably be to create separate shares, one authenticated share and one open share.

---

### Post by Roasted on 2009-04-13
No no... I actually created a Guest account. There is a guest account on my Ubuntu system and I then added it to Samba.

Would that interfere with anything?

---

### Post by dmizer on 2009-04-13
Possibly, does the guest account have another name other than "guest"?

It will still help to see your /etc/samba/smb.conf file.

---

### Post by nanohead on 2009-04-13
dmizer,

Thanks for all your insight into SAMBA.  You are possibly the only person who actually tries to help us out without throwing us under the bus.   

Each time I install a new version of Ubuntu, I have to spend days (weeks sometimes) getting SAMBA to work bidirectionally again, cuz the devs change things each time they do a new release

It would be nice if someone who knew the subject matter would write an updated "How to configure SAMBA" doc for the current Ubunutu implementation.   I would be more than happy to do it, if I understood the detailed subject matter.

---

### Post by Roasted on 2009-04-13
My smb.conf:

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
	workgroup = workgroup

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
	create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
	directory mask = 0775

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

	username map = /etc/samba/smbusers
	security = user
;	guest ok = no
;	guest account = nobody
;	guest ok = no
;	guest account = nobody

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



[Jason]
	path = /home/jason
	writeable = yes
;	browseable = yes
	valid users = jason

[Tyler]
	path = /media/storage/tyler
	writeable = yes
;	browseable = yes
	valid users = jason, tyler
	force group = sambashare

[Curt]
	path = /media/storage/curt
	writeable = yes
;	browseable = yes
	valid users = curt, jason
	force group = sambashare

[Pam]
	path = /media/storage/pam
	writeable = yes
;	browseable = yes
	valid users = jason, pam
	force group = sambashare

[Public]
	path = /media/storage/public
	writeable = yes
;	browseable = yes
	valid users = curt, guest, jason, pam, tyler
	force group = sambashare

[Spare_Storage]
	path = /media/storage/spare_storage
	writeable = yes
;	browseable = yes
	valid users = guest, jason, x
	force group = sambashare
```

What I was testing was jason (myself) versus guest. Guest, as you can see, only has access to public and spare storage. I use public to transfer files with friends, where spare_storage is what I use if I work on a friend's computer and have to back their stuff up, that's where it goes - to spare_storage.

What I did exactly was the following:

 - On XP Laptop wired to the network, I went to my Samba server via start - run - \\skynet (my ubuntu computer name) and clicked on "spare_storage".

 - It then asked me to log in. I logged in as myself, Jason.

 - I created a bogus folder named "test". In Ubuntu, this "test" folder came up with 775 octal permissions and jason:sambashare as the owner.

*GUEST IS NOT A PART OF SAMBASHARE GROUP*

 - I rebooted XP laptop, powered up, logged in as guest, and was able to edit the "test" folder accordingly.

My question is this:

Do octal rights only apply to my Ubuntu computer in particular? Or do the octal rights carry over to Samba shares? Reasoning is, if octal rights only apply to my local computer, it would make sense why "Guest" was able to edit "Jason's" test folder, because guest/jason both have access to that folder, both read/write, so it would make sense. BUT, if octal rights DO carry over to Samba shares, when guest should have been locked out from editing that folder whatsoever.

---

### Post by bab1 on 2009-04-13
> **Roasted said:**
> 
What I was testing was jason (myself) versus guest. Guest, as you can see, only has access to public and spare storage. I use public to transfer files with friends, where spare_storage is what I use if I work on a friend's computer and have to back their stuff up, that's where it goes - to spare_storage.

What I did exactly was the following:

 - On XP Laptop wired to the network, I went to my Samba server via start - run - \\skynet (my ubuntu computer name) and clicked on "spare_storage".

 - It then asked me to log in. I logged in as myself, Jason.

 - I created a bogus folder named "test". In Ubuntu, this "test" folder came up with 775 octal permissions and jason:sambashare as the owner.

*GUEST IS NOT A PART OF SAMBASHARE GROUP*

 - I rebooted XP laptop, powered up, logged in as guest, and was able to edit the "test" folder accordingly.

My question is this:

Do octal rights only apply to my Ubuntu computer in particular? Or do the octal rights carry over to Samba shares? Reasoning is, if octal rights only apply to my local computer, it would make sense why "Guest" was able to edit "Jason's" test folder, because guest/jason both have access to that folder, both read/write, so it would make sense. BUT, if octal rights DO carry over to Samba shares, when guest should have been locked out from editing that folder whatsoever.

Octal rights (permissions) do apply to the user who is logged in to the Samba share.  The Samba user is either a user (or mapped to a user) on the host where Samba is running anyway.

There are times where you have authorization to read or write but not the permission to do so.  In addition 775 give others (world) read and execute rights to the folder.  So anyone could create files in the folder.

---

### Post by dmizer on 2009-04-13
> **Roasted said:**
> Do octal rights only apply to my Ubuntu computer in particular? Or do the octal rights carry over to Samba shares? Reasoning is, if octal rights only apply to my local computer, it would make sense why "Guest" was able to edit "Jason's" test folder, because guest/jason both have access to that folder, both read/write, so it would make sense. BUT, if octal rights DO carry over to Samba shares, when guest should have been locked out from editing that folder whatsoever.
Octal rights carry over to samba shares, but samba handles permissions when the share is created.

Since your Spare_Storage share is explicitly given permission to both Jason and Guest, both Jason and Guest are given permission to all the shared folders under Spare_Storage. So when Jason created the test folder, samba gave Guest permission to it.

This is how you've designed your share. You can't give both Jason and Guest full read/write permission to Spare_Storage but prevent Guest from editing a folder created by Jason.

---

### Post by Roasted on 2009-04-13
> **dmizer said:**
> Octal rights carry over to samba shares, but samba handles permissions when the share is created.

Since your Spare_Storage share is explicitly given permission to both Jason and Guest, both Jason and Guest are given permission to all the shared folders under Spare_Storage. So when Jason created the test folder, samba gave Guest permission to it.

This is how you've designed your share. You can't give both Jason and Guest full read/write permission to Spare_Storage but prevent Guest from editing a folder created by Jason.

Okay, yeah, that's fine. This wasn't about what I wanted to do with each user, I just wanted to understand how it was working here.

So more or less, because I granted guest + jason access to spare_storage, they can do whatever the octal rights are for that folder. I got it. 

Sounds good. Thanks!

---

