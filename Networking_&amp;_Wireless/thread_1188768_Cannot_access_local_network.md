---
title: "Cannot access local network"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by com64 on 2009-06-16
Howdy! :)

Okay, so I'm not long out of the n00b woods with relation to ubuntu in general, but I *am* intelligent enough to pick up the obvious.  Most of the time, anyway.

I've got a nice, grunty box with a 3-4 day old Jaunty install (upgraded from win 7) running a simple apache webserver (only pointed out for its moderate chance of being relevant).  My mrs is down the hall with her XP box, dying to regain access to all the lovely audio and video files I have stored on local harddrives.

In case you couldnt follow: I have a relatively fresh ubuntu 9.04 that just **WILL NOT** play nice with regard to sharing shared mounted NTFS partitions with WinXP.

[This page]("http://blog.taragana.com/index.php/archive/install-samba-and-share-folder-in-ubuntu-904-jaunty-jackalope/") seems to believe setting up Samba and getting on the network is a simple 3-step process:

Step 1: Install Samba. *DONE*
Step 2: Change workgroup in smb.conf *DONE*
[INDENT]***JUST** workgroup??  Yip. Thats what it says.*[/INDENT]
Step 3: Restart Samba *DONE*

Then, apparently, Places-->Network-->Windows Network, and there's the goodies!

But wait - ***ERROR*: Unable to mount location, Could not retrieve share list from server.**

Yay.  After 8 hours and 35 minutes of trying to find out why (and being too manly to ask for help) I have given in and am posting here begging for a solution (and possibly humility, should it be something completely obvious).

In my hunt, I read a post somewhere that asked the complainee to show the output of the command 'findsmb'.  That user at least showed some entries - mine shows nada:

[INDENT]moochoo@moochoo-pc:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
moochoo@moochoo-pc:~$ [/INDENT]

I'm looking at this output hoping like hell it'll point out to somebody a little more knowledgeable exactly where I've bunged up, or at least give me a place to start.

Any help MUCH appreciated - I will send you flowers, candy and a cute stuffed bunny.

---

### Post by dandnsmith on 2009-06-16
Something you didn't mention doing:
to share files held on the Ubuntu machine, you need share definitions set up in the smb.conf

Another thing which has consistently got me is the firewalls. You can have firewalls each end, and the Ubuntu one may be blocking without your being aware of it. There are log files kept to show attempts to access samba files shared (in /var/log/...)

---

### Post by swerdna on 2009-06-16
findsmb shows nothing there. can you do three things:

[LIST=1]
[*]Please open a console and see what reply you get to this: ```
sudo /etc/init.d/samba status
```
[*]Post the smb.conf file. It's located at /etc/samba/smb.conf
[*]Check in a windows box at Right-click "My Computer" icon --> Properties --> Computer name. What's the workgroup name there?
[/LIST]

---

### Post by superprash2003 on 2009-06-16
take a look at this [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by com64 on 2009-06-16
Regarding the entries in smb.conf - didnt work with or without them.  ATM the mounts are shared via right-clicking, then selecting 'Sharing Options' in Nautilus.  If I smb://192.168.1.50 I can now see the folders shared on the XP box, and if I smb://192.168.1.2 (this machine) I can view the mount points I have shared.  WinXP can't see anything, of course.

What port(s) do I need to forward thru the firewalls?

If all else fails I could just put the data drives from this box into the XP box (I can see it but it cant see me) so the data will at least be accessible from both machines.

```
moochoo@moochoo-pc:~$ sudo /etc/init.d/samba status
 * nmbd is running
 * smbd is running
moochoo@moochoo-pc:~$ 

```

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
   workgroup = MSHOME

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

;[printers]
;   comment = All Printers
;   browseable = no
;   path = /var/spool/samba
;   printable = yes
;   guest ok = no
;   read only = yes
;   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
;[print$]
;   comment = Printer Drivers
;   path = /var/lib/samba/printers
;   browseable = yes
;   read only = yes
;   guest ok = no
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

```

---

### Post by swerdna on 2009-06-16
here are the contents of your smb.conf file (distilled by running it through testparm):
> [global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
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
There is only a [global] stanza. As you noted, there are no shares configured there. As you also noted, the shares that you made have been generated with the Nautilus share tool, and so they are not classical shares that appear in smb.conf. Rather, they are "usershares" and their config goes into /var/lib/samba/usershares.

There are two likely problems in smb.conf. One is that it's not properly configured for usershares (see below). The second problem is that name resolution is not properly configured. I suggest that you back smb.conf up with this Gnome terminal command:```

sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup
```
And that you then edit the file with this command:```
gksudo gedit /etc/samba/smb.conf
```
And that you replace the old contents with these contents:
```
[global]
workgroup = MSHOME
server string = %h server (Samba, Ubuntu)
map to guest = Bad User
netbios name = name_of_this_workstation
name resolve order = bcast host lmhosts wins
local master = yes
preferred master = yes
os level = 65
usershare allow guests = Yes
usershare max shares = 100
usershare owner only = False
```
replace "name_of_this_workstation" with a network name for the Ubuntu computer, whatever you like, short, preferably no spaces.

Then restart the Ubuntu computer and the windows computer, successively. See whether you can find your shares that you generated with Nautilus with this command: ```
smbtree -N
```If you can see them then you made them properly. If you can't see them with "smbtree -N", then you'll need to remake them.

Then try the view from windows.

PS edit -- Oh and of course, to make things diagnostically easier, turn of any Linux firewall/s for the time being.

---

### Post by com64 on 2009-06-16
> **swerdna said:**
> 
PS edit -- Oh and of course, to make things diagnostically easier, turn of any Linux firewall/s for the time being.

*facepalm* working now :)

Seems the firewall I configured to allow stuff thru one port was blocking every other port... *doh*  It's amazing how you can get so stuck into something complicated that you miss the basics.

Thanks for your help man :)

---

### Post by swerdna on 2009-06-16
Excellent, glad it's going

---

