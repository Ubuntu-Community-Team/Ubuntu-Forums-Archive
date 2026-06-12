---
title: "Sharing mounted Ntfs"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by jafarul on 2010-06-21
i have a folder in my ntfs drive. i want to share it. most of pc in my network is using windows. used samba. it is shared, user can see the folder but when click "You dont have th permission to access this folder.

tried Sudo chmod 
tried [This]("http://www.debuntu.org/guest-file-sharing-with-samba")

ant idea? :p

---

### Post by Morbius1 on 2010-06-21
Post the output of the following commands since we don't know what method of samba sharing you're using nor do we know how you are mounting the ntfs opartition:

```
net usershare info
sudo net usershare info
testparm -s
cat /etc/fstab
```

---

### Post by jafarul on 2010-06-21
[B]net usershare info
================[/B]
[shared]
path=/media/Hiburan/Shared Folder
comment=
usershare_acl=Everyone:F,
guest_ok=y

[B]testparm -s
============[/B]
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[Shared Folder]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
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
	guest ok = Yes

[Shared Folder]
	comment = Guest access share
	path = /media/Hiburan/Shared Folder
	read only = No

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

[B]cat /etc/fstab
=============[/B]
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=c276c5a7-d032-4a64-a990-a147ae2ccda0 /home           ext4    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=5380b361-e41e-4269-98c9-9ad77bf84776 none            swap    sw              0       0



[I]Sorry... here it is
*Note - "Hiburan" is the NTFS-HDD
      - "Share Folder is the folder that im trying to share[/I]

---

### Post by Morbius1 on 2010-06-21
You've got two problems. There are two ways to use samba to create shares. You're using both on the same target:
This is a Nautilus-share:
> [shared]
path=/media/Hiburan/Shared Folder
comment=
usershare_acl=Everyone:F,
guest_ok=y
This is a Classic-share:
> [Shared Folder]
    comment = Guest access share
    path = /media/Hiburan/Shared Folder
    read only = NoThe nautilus-share is allowing write access to guests. The classic share is allowing write but only to those who have the correct username and password.

Which one do you want?

---

### Post by jafarul on 2010-06-21
I think i'll go with Nautilus-share. hmmm how am i suppose to fix this?

---

### Post by Morbius1 on 2010-06-21
In a terminal type:
```
gksu gedit /etc/samba/smb.conf
```Add the following line under the [global] section of smb.conf:
```
force user = morbius
```[COLOR=Blue]*Change morbius to you own login user name*[/COLOR]

Now find this share definition towards the bottom of the file:
> [Shared Folder]
    comment = Guest access share
    path = /media/Hiburan/Shared Folder
    read only = Noand place # signs in front of each line so that it looks like this:
```

#[Shared Folder]
#comment = Guest access share
#path = /media/Hiburan/Shared Folder
#read only = No
```Save the file, exit gedit, and back in the terminal type:
```
sudo service smbd restart
```

---

### Post by jafarul on 2010-06-21
yeah it works!!! thnx!!

---

### Post by jafarul on 2010-06-27
[COLOR="RoyalBlue"]ok.. i was setting up the auto mount configuration. after a while my folder stopped sharing. 
here again are my setting as you requested in the previous thread[/COLOR]


xeroz@xeroz-desktop:~$ net usershare info
[2010/06/28 03:56:14,  0] param/loadparm.c:7472(lp_do_parameter)
  Ignoring unknown parameter "sershare owner only"
info_fn: file /var/lib/samba/usershares/shared is not a well formed usershare file.
info_fn: Error was Path is not a directory.
xeroz@xeroz-desktop:~$ sudo net usershare info
[2010/06/28 03:56:27,  0] param/loadparm.c:7472(lp_do_parameter)
  Ignoring unknown parameter "sershare owner only"
xeroz@xeroz-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Unknown parameter encountered: "sershare owner only"
Ignoring unknown parameter "sershare owner only"
Processing section "[Shared Folder]"
WARNING: No path in service Shared Folder - making it unavailable!
NOTE: Service Shared Folder is flagged unavailable.
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
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	force user = xeroz
	guest ok = Yes

[Shared Folder]
	available = No

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
xeroz@xeroz-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
/dev/sdb1      /media/mpoint ntfs-3g    default  0   0
# /home was on /dev/sda3 during installation
UUID=c276c5a7-d032-4a64-a990-a147ae2ccda0 /home           ext4    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=5380b361-e41e-4269-98c9-9ad77bf84776 none            swap    sw              0       0

**[COLOR="RoyalBlue"]screenshot of the error[/COLOR]**
[IMG]http://img341.imageshack.us/img341/305/folderl.png[/IMG]

[COLOR="RoyalBlue"]sorry for the trouble[/COLOR]

---

### Post by Morbius1 on 2010-06-27
Please post the output of the following commands:
```
cat /etc/samba/smb.conf
cat /var/lib/samba/usershares/shared
```

---

### Post by jafarul on 2010-06-27
[B]cat /etc/samba/smb.conf
========================[/B]

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
sershare owner only = false
force user = xeroz
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
;   interfaces = lo eth0

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

#   security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;	encrypt passwords = yes

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
	security = user
	guest ok = yes
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

[Shared Folder]
#	comment = Guest access share
#	path = /media/Hiburan/Shared Folder
#	browseable = yes
#	writeable = yes
#	guest ok = yes

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

[B]cat /var/lib/samba/usershares/shared
===================================[/B]

#VERSION 2
path=/media/Hiburan/Shared Folder
comment=
usershare_acl=S-1-1-0:F
guest_ok=y

---

### Post by Morbius1 on 2010-06-27
```
gksu gedit /etc/samba/smb.conf
```Look for this section:
> [FONT=monospace]#======================= Global Settings =======================

[global]
[COLOR=Blue]sershare owner only = false[/COLOR]
force user = xeroz
## Browsing/Identification ###[/FONT]Change [COLOR=Blue]sershare[/COLOR] to [COLOR=Blue]usershare

[COLOR=Black]Next find this section:
[/COLOR][/COLOR]> [COLOR=Blue][Shared Folder][/COLOR]
# comment = Guest access share
# path = /media/Hiburan/Shared Folder
# browseable = yes
# writeable = yes
# guest ok = yesPlace a # in front of [COLOR=Blue][Shared Folder]

[COLOR=Black]Save smb.conf, exit gedit, and back in the terminal type:
[/COLOR][/COLOR]```
[COLOR=Black]sudo service smbd restart[/COLOR]
```[COLOR=Blue][COLOR=Black]

What's not entirely clear to me is if the path: [/COLOR][/COLOR]/media/Hiburan/Shared Folder still exists.

If it does not then you can remove the share it's referencing by issuing this command in a Terminal:
```
net usershare delete shared
```When all that's done try to share /media/mpoint/Shared Folder.

If you still have errors then post the dynamic duo again:
```
net usershare info
testparm -s
```

---

### Post by jafarul on 2010-06-28
**net usershare info**
info_fn: file /var/lib/samba/usershares/shared is not a well formed usershare file.

**testparm -s**

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
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
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d
	force user = xeroz
	guest ok = Yes

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

**is there anyway for me to reset this and start all over again?btw the folder that im tryring to share /media/Hiburan/Share Folder** :rolleyes:

---

### Post by Morbius1 on 2010-06-28
> **btw the folder that im tryring to share /media/Hiburan/Share Folder**  That's where I'm getting confused.
> info_fn: file [COLOR=Blue]/var/lib/samba/usershares/shared[/COLOR] is not a well formed  usershare file.
info_fn: [COLOR=Blue]Error was Path is not a directory[/COLOR].> cat [COLOR=Blue]/var/lib/samba/usershares/shared[/COLOR]
===================================

#VERSION 2
path=/media/Hiburan/Shared Folder
comment=
usershare_acl=S-1-1-0:F
guest_ok=y It looks like /media/Hiburan/Shared Folder doesn't exist.

And your "screenshot of the error" indicates you're trying to share:
/media/mpoint/Shared Folder.

---

### Post by jafarul on 2010-06-28
anyway after following your previous instruction then open up nautilus, i right click > sharing option. i work fine now. Anyway thank you. you've been a big help :p

---

