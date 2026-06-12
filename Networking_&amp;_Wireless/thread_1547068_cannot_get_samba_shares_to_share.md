---
title: "cannot get samba shares to share"
date: 2010-08-06
forum: Networking &amp; Wireless
---

### Post by jdawgvh on 2010-08-06
I am trying to create a Samba share on Ubuntu so that I can see it on my Windows computer but have had nothing but trouble.  I've tried everything that I could find in Google but the best I can get is that my Ubuntu computer shows up as Unknown device on my Windows computer.  Unfortunately, my Windows computer belongs to my company or I would just switch to Ubuntu altogether.  I have posted a couple of screenshots of what I see in Windows, my GParted partitions, and the options that I have enabled for the folder I am trying to share.  Below are my fstab and my samba files from Ubuntu.  I am sure that this is just some rookie mistake as I am new to Ubuntu.  It certainly seems that this should be easy, but I just can't get it.  Any help would be appreciated.

Thanks!


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdb1 :
UUID=0de6734b-d7ec-4661-b3c2-3d8afc46a04b	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda1 :
UUID=53A25C417E57014F	/media/Storage	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sdb5 :
UUID=11cd3634-7bef-4872-8b23-248770f171b2	none	swap	sw	0	0








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

usershare owner only = False

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

---

### Post by YesWeCan on 2010-08-06
I usually try to simplify as much as possible when something isn't working and once the simple version works I add to it: [http://oreilly.com/catalog/samba/chapter/book/ch02_04.html](http://oreilly.com/catalog/samba/chapter/book/ch02_04.html)

---

### Post by jdawgvh on 2010-08-25
Ok, I went through the whole manual (I have been travelling and so have not had time to spend on this until now).  It seems as though something significant has changed in this most recent release of Ubuntu.  I don't seem to be the only one with the problem of not being able to share folders.  Has anyone come up with a solution for this?  I have tried just about every smb.conf configuration that I could find on the internet, allowing guest access or not and still cannot see my shares from my other computers (Mac, Windows and Ubuntu on another computer cannot see the shares).  I have tried using the Samba GUI and without.  Thinking I corrupted something, I reloaded Ubuntu on my machine and started over.  Nope, it wasn't me.  Samba doesn't seem to work for me.  Can someone please tell me what I am doing wrong?  It doesn't seem like it should be so difficult to simply create a share on a computer.  Currently my computer is set up as explained in this tutorial:

[http://www.jonathanmoeller.com/screed/?p=1590]("http://www.jonathanmoeller.com/screed/?p=1590")

---

### Post by endotherm on 2010-08-25
well, what I have found, is that it is never a good idea to mix classic samba configuration (manual entry in the smb.conf) and the userspace nautilus-share (the gui sharing).

what is the output of 
```

sudo testparm
net usershare info

```

btw here is a cleaned up copy of your smb.conf. much easier to read. why is security = user commented out?
```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###
workgroup = WORKGROUP
server string = %h server (Samba, Ubuntu)
dns proxy = no
usershare owner only = False
#### Debugging/Accounting ####
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d

####### Authentication #######
# security = user
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
map to guest = bad user

############ Misc ############
usershare allow guests = yes

#======================= Share Definitions =======================
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
```

---

### Post by jdawgvh on 2010-08-28
the folder that I am trying to share is on a second hard disk mounted on my Ubuntu box.  Does it matter if it is NTFS or EXT4?  I have tried both but I have tried so many variations that I don't know what works and what doesn't.  Why the security = user line is commented out I don't know.  I will turn it back on.  Here is the output that you asked for:


administrator@administrator-desktop:~$ sudo testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Storage]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	guest account = administrator
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = bcast host lmhosts wins
	os level = 33
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
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

[Storage]
	comment = Photo/Video media storage
	path = /media/Storage
	read only = No
administrator@administrator-desktop:~$ net usershare info
administrator@administrator-desktop:~$ 


Thank you for your help!

---

### Post by jdawgvh on 2010-08-30
new update:  since I was having so much trouble with getting a folder to share I did a little more digging.  I found this in the bug reports:

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610")

This is more or less the problem I had but the fix that they suggest did not work.  You are going to laugh when you hear what I did, but I did get it to work.  I downloaded a copy of Hardy Heron and installed that on my computer, then set up my folders and my sharing using Samba in Hardy Heron.  It worked right out of the box.  Next I am going to upgrade my computer to the latest version (saving my smb.conf file on a flash drive) and see if I can get it to work in the new version.

---

### Post by endotherm on 2010-08-31
I thought I posted this a few days ago, but now i'm not seeing a post.... i see you got it working with hardy, so thats good. if you ever want to revisit lucid, these remarks may be of use. otherwise happy ubuntuing.

have you tried uncommenting "Security = user" and restarting samba?
```

sudo service smbd restart

```
after that have you used smbpasswd to authorize your user for samba access?
```
sudo smbpasswd -a <username>
```

the bug you have linked, is a problem with naming resolution, which doesn't really impact the creation of a share. I think the reporter conflated some issues to get a linear narritive of the issue. in his case, he created a share, but no one on a remote machine could see it for a minute or so. the network just hadn't quite realized it was there yet. they "fixed" that by making broadcast the default first try mechanism (which is rather inefficient in all cases except the very narrow circumstances described).

---

### Post by jdawgvh on 2010-09-01
Ok, I went out on a limb.  I copied my Hardy Heron smb.conf file (below) and reinstalled 10.04.  Everything does work which means that I was doing something wrong the whole time.  Here is the smb.conf that I ended up with that works like a champ:

[global]
workgroup = WORKGROUP
netbios name = Storage Server
encrypt passwords = true
security = user

[Storage]
path = /media/Storage
browseable = yes
read only = no

Thanks so much for your help!  I do have one follow up question though.  My log in name (on Linux) is Storage.  I was unable to create any users for Samba other than Storage.  Is there a way to create more users somehow?

---

### Post by endotherm on 2010-09-01
> **jdawgvh said:**
> Ok, I went out on a limb.  I copied my Hardy Heron smb.conf file (below) and reinstalled 10.04.  Everything does work which means that I was doing something wrong the whole time.  Here is the smb.conf that I ended up with that works like a champ:

[global]
workgroup = WORKGROUP
netbios name = Storage Server
encrypt passwords = true
security = user

[Storage]
path = /media/Storage
browseable = yes
read only = no

Thanks so much for your help!  I do have one follow up question though.  My log in name (on Linux) is Storage.  I was unable to create any users for Samba other than Storage.  Is there a way to create more users somehow?

sure. just create a user through the ubuntu users control applet (system administration users). then once the use is created and the password set, run this command to register the user with samba:
```
sudo smbpasswd -a <newusername>

``` and set the password (same as the Unix password you set when creating the user) when prompted. 

the folder you share will have to have permissions that will allow the new user to access them. to do this, i add all my smb users to a group. that way my files are owned by admin:smbusers with permissions of at least 640. I also tend to set GID on the share directories so that everything is created as being owned by the smbusers group, and on some shares I add the sticky bit to allow users to create and delete their own files, but no one elses.
heres some info on extended permissions:
[http://docs.sun.com/app/docs/doc/816-4557/secfile-69?a=view](http://docs.sun.com/app/docs/doc/816-4557/secfile-69?a=view)
remember you are setting this on a folder (special perms work differently on files than they do on folders).

---

