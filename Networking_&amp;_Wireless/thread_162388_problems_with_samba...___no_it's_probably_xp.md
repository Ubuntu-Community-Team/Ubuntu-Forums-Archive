---
title: "problems with samba...   no it's probably xp"
date: 2006-04-18
forum: Networking &amp; Wireless
---

### Post by Craig Caldwell on 2006-04-18
I've been at this for a long time today and seem to be up against a ](*,) . Here is my smb.conf. 
I am able to see and access my shared folder on the xp box from the ubuntu box but not the other way arround. I can see but not access the ubuntu shared files from the xp box. I click on a folder in the windows network places... then I'm asked for a password then nothing happens. No errors, no access, nothing.I'm not sure what do do at this point. I've folowed every thing that I could find in the forums.


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
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = Rae_rd

# server string is the equivalent of the NT Description field
   server string = l-opteron

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

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
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
   security = user username map = /etc/samba/smbusers

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

+########## Domains ###########

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
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

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
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @ntadmin


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

wins support = yes
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
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
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

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



[Music]
path = /home/craig/Music
comment = multiple file formats
   public = yes
   writable = no
   valid users = system_username1 system_username2
   create mask = 0700
   directory mask = 0700
   force user = nobody
   force group = nogroup
   


[allofmp3]
path = /home/craig/allofmp3
comment = 160 ogg vorbis
   public = yes
   writable = no
   valid users = system_username1 system_username2
   create mask = 0700
   directory mask = 0700
   force user = nobody
   force group = nogroup
   


[shared_items]
path = /home/craig/shared_items
comment = anything not music
   public = yes
   writable = no
   valid users = system_username1 system_username2
   create mask = 0700
   directory mask = 0700
   force user = nobody
   force group = nogroup
   


[ogg_music]
path = /home/craig/ogg_music
comment = 160 ogg vorbis
   public = yes
   writable = no
   valid users = system_username1 system_username2
   create mask = 0700
   directory mask = 0700
   force user = nobody
   force group = nogroup
   


```

---

### Post by Nequeo on 2006-04-18
[QUOTE=Craig Caldwell]I've been at this for a long time today and seem to be up against a ](*,) . Here is my smb.conf. 
I am able to see and access my shared folder on the xp box from the ubuntu box but not the other way arround. I can see but not access the ubuntu shared files from the xp box. I click on a folder in the windows network places... then I'm asked for a password then nothing happens. No errors, no access, nothing.I'm not sure what do do at this point. I've folowed every thing that I could find in the forums.
[/QUOTE]

Try this... From your Ubuntu box open a terminal and type:

"sudo smbpasswd -a $user"

where $user is the name of a user that exists on your Ubuntu system. Then you'll be prompted for a password. (It doesn't have to be the same as their Linux logon password)

Go back to the Windows box and put in the username and the password you just set. 

You might also want to try commenting out the 'valid users' line from all your shares and restarting samba. Lemme know how it goes.

---

### Post by Nequeo on 2006-04-18
Just remembered (been a long time since I've done a Samba set-up...):

Windows caches your login details. So if you add a user to your linux machine with the same username you use under Windows - and give it the same password using 'smbpasswd -a', then you won't get prompted for a username and password to connect. It'll just go straight through.

If you still have issues after all that, it might be related to the 'Simple File Sharing' config switch in Windows. But we'll worry about that later (if you have the Home edition of XP).

---

### Post by Craig Caldwell on 2006-04-19
aaaaahhhhh... I'm back from a nice swim. Now back to work.
here is another file that I can't make heads or tails of.  testparm
```
craig@l-opteron:~$ sudo smbpasswd -a craig
Password:
New SMB password:
Retype new SMB password:
craig@l-opteron:~$ sudo testparm
Load smb config files from /etc/samba/smb.conf
params.c:Parameter() - Ignoring badly formed line in configuration file:  +########## Domains ###########
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Music]"
Processing section "[allofmp3]"
Processing section "[shared_items]"
Processing section "[ogg_music]"
Loaded services file OK.
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = RAE_RD
        server string = l-opteron
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sU NIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        wins support = Yes
```

---

### Post by Craig Caldwell on 2006-04-19
Thank you Nequeo!!! 

I had sudosmbpsswd craig and entered my password before.
So it may have been adding -a that did the trick.
I also commented out the valid user lines. Now I wasn't even prompted for a password to access the shared files.

I managed to get the printer sharing going earlier today so i think this was the final piece in my ubuntu desktop. Now all I need is support for java and flash in 64 bit.

Nequeo, if it isn't too much to ask could you give me a quick heads up on why commenting out the "valid users" and adding -a to the user name made all the difference?
Thanks for your help.

---

### Post by Nequeo on 2006-04-19
[QUOTE=Craig Caldwell]Thank you Nequeo!!! 

I had sudosmbpsswd craig and entered my password before.
So it may have been adding -a that did the trick.
I also commented out the valid user lines. Now I wasn't even prompted for a password to access the shared files.

I managed to get the printer sharing going earlier today so i think this was the final piece in my ubuntu desktop. Now all I need is support for java and flash in 64 bit.

Nequeo, if it isn't too much to ask could you give me a quick heads up on why commenting out the "valid users" and adding -a to the user name made all the difference?
Thanks for your help.[/QUOTE]

The -a option stands for 'add user to the samba database'. Smbpasswd on its own, without the -a, will let you change the password for an existing user in the Samba database... but if that user hasn't been added yet, there ain't much point! :) 

I'm no Samba expert, so I'm not entirely sure what the valid user lines are for (though the documentation on [www.samba.org](www.samba.org) is very helpful). But my guess is that it is a list of users who are allowed to connect to your shares. Taking it out probably will default to a sensible "anyone who is listed in my password database" default.

Hope that helps,

---

