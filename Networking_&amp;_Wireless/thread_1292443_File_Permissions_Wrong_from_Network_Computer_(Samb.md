---
title: "File Permissions Wrong from Network Computer (Samba)"
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by mkw87 on 2009-10-15
I have had Ubuntu installed on a media serving computer for over 2 years, and never had ANY trouble out of it.  Every month or two I would update regularly, no problem.  About 4 months ago (guess) I updated and ran into issues with Samba.  

Now when I create a file on the media server from a laptop or my desktop, the file has ownership of the Samba account, not the Server account.  This was never the case before.  I have not been able to figure out what is causing this; below is my smb.conf:

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

[downloads]
    path = /home/server/media/downloads
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0755
    directory mask = 0755
    force user = matthew
;    force group = server

[media]
    path = /home/server/media
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0755
    directory mask = 0755
    force user = matthew
;    force group = server


[backup]
    path = /home/server/backup
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0755
    directory mask = 0755
    force user = matthew
;    force group = sambashare

[backup2]
    path = /home/server/backup2
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0755
    directory mask = 0755
    force user = matthew
;    force group = sambashare

```

This error annoyed me enough to upgrade to the newest version of Ubuntu in hopes of fixing it, so I did a network upgrade.  I have changed the masks on the directory, I have deleted and recreated the user and group I use for Samba, but cannot figure out what the problem is.  Any ideas short of the typical windows-style fix of formatting and a fresh install?

---

### Post by swerdna on 2009-10-16
I would make the shares like this:
[backup]
	path = /home/server/backup
	force user = matthew
	read only = No
And I would chown the directory matthew (and its contents) over to group=matthew, owner=matthew. I would chmod everything to 755 or 750. That way the share and its contents would behave exactly as if the owner was matthew. That's implicit in the use of the force user parameter.

And similarly for the other file shares.

FFI see "Share #8 - imposing uniform ownership with the force user parameter" in this tutorial:
[Samba Server and Ubuntu / Kubuntu: HowTo Configure a Professional File Server on a SOHO LAN]("http://ubuntu.swerdna.org/ubusambaserver.html#shares")

---

### Post by mkw87 on 2009-10-18
> **swerdna said:**
> I would make the shares like this:
[backup]
	path = /home/server/backup
	force user = matthew
	read only = No
And I would chown the directory matthew (and its contents) over to group=matthew, owner=matthew. I would chmod everything to 755 or 750. That way the share and its contents would behave exactly as if the owner was matthew. That's implicit in the use of the force user parameter.

And similarly for the other file shares.

FFI see "Share #8 - imposing uniform ownership with the force user parameter" in this tutorial:
[Samba Server and Ubuntu / Kubuntu: HowTo Configure a Professional File Server on a SOHO LAN]("http://ubuntu.swerdna.org/ubusambaserver.html#shares")

I will give this a try.  I forgot to mention Matthew is the username for my samba user......"server" is the username for the account on the linux server (matthew = windows login, if I use same password then I autologin to linux server).

Thank you.

---

### Post by mkw87 on 2009-10-18
Ok, I had to chmod everything to 777 and set up my smb.conf like this for the shares:

```

[share]
path = /home/server/share
read only = no
force user = server

```

Thanks for the link........it said I should have to chmod 750 to accomplish what I wanted, which is what you said, but it did not work if I did it 750.......only 777. Thanks.

---

### Post by swerdna on 2009-10-18
> **mkw87 said:**
> I will give this a try.  I forgot to mention Matthew is the username for my samba user......"server" is the username for the account on the linux server (matthew = windows login, if I use same password then I autologin to linux server).

Thank you.

Force user can only work if matthew is a real Ubuntu user. Matthew can also be a windows user, but that's immaterial to the "force user" tool. So for a network that does what you want, add an Ubuntu user matthew, then you won't need 777.

---

### Post by mkw87 on 2009-10-18
> **swerdna said:**
> Force user can only work if matthew is a real Ubuntu user. Matthew can also be a windows user, but that's immaterial to the "force user" tool. So for a network that does what you want, add an Ubuntu user matthew, then you won't need 777.
matthew is an ubuntu user as well.......I just never login to it.  It does exist in Users though.

---

### Post by swerdna on 2009-10-19
> **mkw87 said:**
> matthew is an ubuntu user as well.......I just never login to it.  It does exist in Users though.

Could be something strange with the ownership. What's the return from this command:```
 ls -l /home/server | grep share
```

---

### Post by mkw87 on 2009-10-22
drwxrwxr-x 12 server matthew 4096 DATE TIME media

---

### Post by swerdna on 2009-10-22
> **mkw87 said:**
> drwxrwxr-x 12 server matthew 4096 DATE TIME media

And therein lies the issue. Remember this:> And I would chown the directory matthew (and its contents) over to group=matthew, owner=matthew.

You have group=matthew, owner=server

---

