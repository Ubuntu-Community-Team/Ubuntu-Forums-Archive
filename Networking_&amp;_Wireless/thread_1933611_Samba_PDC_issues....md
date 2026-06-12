---
title: "Samba PDC issues..."
date: 2012-02-29
forum: Networking &amp; Wireless
---

### Post by Stonewahl on 2012-02-29
Hi all! Im hoping I can get some assistance with a Samba PDC setup that I  have. I saw a few other threads on this site that seemed to have gotten  some decent answers so I am really banking that you guys can help me  solve this.

I have Samba setup on a home server running Ubuntu. I have two users and  a total of 5 machines that will be using the network. All machines are  running Windows 7 and have the appropriate registry fixes applied that  let them talk to the Samba server.

The issue is that recently one of the users cannot logon to the domain  controller intermittently. Sort of a shot in the dark one way or the  other as to whether or not it worked. I did some research and found that  maybe the user was not set to the correct Domain and come to find out  that the user with the issues WAS set to the right one but the user  without issues was not. I changed the problem user to the same domain as  the other and now they can login, but profiles are not roaming for  either user.

So, here is the result of running  	Code:
 	sudo pdbedit -L -v | less 
:

 	Code:
 	---------------
Unix username:        nobody
NT username:          
Account Flags:        [U          ]
User SID:             S-1-5-21-968941708-1228548467-2506160436-501
Primary Group SID:    S-1-5-21-968941708-1228548467-2506160436-513
Full Name:            nobody
Home Directory:       
HomeDir Drive:        (null)
Logon Script:         
Profile Path:         
Domain:               FAMILY
Account desc:         
Workstations:         
Munged dial:          
Logon time:           0
Logoff time:          never
Kickoff time:         never
Password last set:    0
Password can change:  0
Password must change: 0
Last bad password   : 0
Bad password count  : 0
Logon hours         : FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
---------------
Unix username:        lindsay
NT username:          
Account Flags:        [U          ]
User SID:             S-1-5-21-968941708-1228548467-2506160436-1000
Primary Group SID:    S-1-5-21-968941708-1228548467-2506160436-513
Full Name:            Lindsay
Home Directory:       \\server\lindsay
HomeDir Drive:        H:
Logon Script:         logon.cmd
Profile Path:         \\server\lindsay\profile
Domain:               WAHL
Account desc:         
Workstations:         
Munged dial:          
Logon time:           0
Logoff time:          Wed, 06 Feb 2036 10:06:39 EST
Kickoff time:         Wed, 06 Feb 2036 10:06:39 EST
Password last set:    Fri, 24 Feb 2012 08:28:16 EST
Password can change:  Fri, 24 Feb 2012 08:28:16 EST
Password must change: never
Last bad password   : 0
Bad password count  : 0
Logon hours         : FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
---------------
Unix username:        RYANLAPTOP$
NT username:          
Account Flags:        [W          ]
User SID:             S-1-5-21-968941708-1228548467-2506160436-1002
Primary Group SID:    S-1-5-21-968941708-1228548467-2506160436-513
Full Name:            RYANLAPTOP$
Home Directory:       \\server\ryanlaptop_
HomeDir Drive:        H:
Logon Script:         logon.cmd
Profile Path:         \\server\ryanlaptop_\profile
Domain:               FAMILY
Account desc:         
Workstations:         
Munged dial:          
Logon time:           0
Logoff time:          Wed, 06 Feb 2036 10:06:39 EST
Kickoff time:         Wed, 06 Feb 2036 10:06:39 EST
Password last set:    Sat, 25 Feb 2012 09:39:29 EST
Password can change:  Sat, 25 Feb 2012 09:39:29 EST
Password must change: never
Last bad password   : 0
Bad password count  : 0
Logon hours         : FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
---------------
Unix username:        rwahl
NT username:          
Account Flags:        [U          ]
User SID:             S-1-5-21-968941708-1228548467-2506160436-1004
Primary Group SID:    S-1-5-21-968941708-1228548467-2506160436-512
Full Name:            rwahl
Home Directory:       \\server\rwahl
HomeDir Drive:        H:
Logon Script:         logon.cmd
Profile Path:         \\server\rwahl\profile
Domain:               FAMILY
Account desc:         
Workstations:         
Munged dial:          
Logon time:           0
Logoff time:          Wed, 06 Feb 2036 10:06:39 EST
Kickoff time:         Wed, 06 Feb 2036 10:06:39 EST
Password last set:    Sun, 26 Feb 2012 22:15:04 EST
Password can change:  Sun, 26 Feb 2012 22:15:04 EST
Password must change: never
Last bad password   : 0
Bad password count  : 0
Logon hours         : FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
---------------
Unix username:        LINDSAYLAPTOP$
NT username:          
Account Flags:        [W          ]
User SID:             S-1-5-21-968941708-1228548467-2506160436-1001
Primary Group SID:    S-1-5-21-968941708-1228548467-2506160436-513
Full Name:            LINDSAYLAPTOP$
Home Directory:       \\server\lindsaylaptop_
HomeDir Drive:        H:
Logon Script:         logon.cmd
Profile Path:         \\server\lindsaylaptop_\profile
Domain:               FAMILY
Account desc:         
Workstations:         
Munged dial:          
Logon time:           0
Logoff time:          Wed, 06 Feb 2036 10:06:39 EST
Kickoff time:         Wed, 06 Feb 2036 10:06:39 EST
Password last set:    Fri, 24 Feb 2012 10:23:37 EST
Password can change:  Fri, 24 Feb 2012 10:23:37 EST
Password must change: never
Last bad password   : 0
Bad password count  : 0
Logon hours         : FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
---------------
Unix username:        DELLDUO-PC$
NT username:          
Account Flags:        [W          ]
User SID:             S-1-5-21-968941708-1228548467-2506160436-1003
Primary Group SID:    S-1-5-21-968941708-1228548467-2506160436-513
Full Name:            DELLDUO-PC$
Home Directory:       \\server\dellduo-pc_
HomeDir Drive:        H:
Logon Script:         logon.cmd
Profile Path:         \\server\dellduo-pc_\profile
Domain:               FAMILY
Account desc:         
Workstations:         
Munged dial:          
Logon time:           0
Logoff time:          Wed, 06 Feb 2036 10:06:39 EST
Kickoff time:         Wed, 06 Feb 2036 10:06:39 EST
Password last set:    Sun, 26 Feb 2012 09:25:49 EST
Password can change:  Sun, 26 Feb 2012 09:25:49 EST
Password must change: never
Last bad password   : 0
Bad password count  : 0
Logon hours         : FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
---------------
Unix username:        ryan
NT username:          
Account Flags:        [U          ]
User SID:             S-1-5-21-968941708-1228548467-2506160436-3000
Primary Group SID:    S-1-5-21-968941708-1228548467-2506160436-513
Full Name:            Ryan
Home Directory:       \\server\ryan
HomeDir Drive:        H:
Logon Script:         logon.cmd
Profile Path:         \\server\ryan\profile
Domain:               WAHL
Account desc:         
Workstations:         
Munged dial:          
Logon time:           0
Logoff time:          Wed, 06 Feb 2036 10:06:39 EST
Kickoff time:         Wed, 06 Feb 2036 10:06:39 EST
Password last set:    Mon, 27 Feb 2012 16:31:43 EST
Password can change:  Mon, 27 Feb 2012 16:31:43 EST
Password must change: never
Last bad password   : 0
Bad password count  : 0
Logon hours         : FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF 
My two users are 'lindsay' and 'ryan'. 'rwahl' was a test user I  created and 'nobody' i have no idea about. 'ryan' and 'lindsay' are both  part of the WAHL domain while all my machines are part of the 'FAMILY'  domain that is specified in my setup file. rwahl when set to the  'FAMILY' domain is unable to login.

Here is my smb.conf file:

 	Code:
 	#======================= Global Settings =======================

[global]
add machine script = /usr/sbin/useradd -n -g machines -d /dev/null -s /sbin/nologin %u

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = family

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
   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
   logon drive = H:
   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
 add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

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
[homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
[netlogon]
   comment = Network Logon Service
   path = /srv/samba/netlogon
   guest ok = yes
   read only = yes
   share modes = no

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
#        cdrom share is accesed. For this to work /etc/fstab must contain
#        an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#        is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom 
I assume there is a giant hole that I am overlooking so any advice would be greatly appreciated! Thanks in advance!

---

