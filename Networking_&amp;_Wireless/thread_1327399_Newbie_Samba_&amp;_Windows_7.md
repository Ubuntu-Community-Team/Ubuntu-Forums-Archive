---
title: "Newbie Samba &amp; Windows 7"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by leemgilbert on 2009-11-15
Hello, I've done a search, but a lot of the threads are over 50 pages from what I've seen and I find it extremely confusing.

 Here goes, I'm a total Linux newbie. I have an oldish laptop that I'm trialling various free OS. I have tried gOS, but it was too unstable, so following the trend have just installed Ubuntu 9.10. 

Okay pulled my hair out sorting my Wireless Broadcom chipset using the terminal.

Last thing though is I can see my Windows 7 HTPC on my Laptop, but I cannot see the shared files it just says "unable to mount" please see below screenshot. I've attached my smb configuration below. Any ideas what's wrong???

[IMG]http://farm3.static.flickr.com/2523/4105416797_35aa3c510d_o.png[/IMG]

> #
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
#   domain master = yes

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


Thank you very much :)

---

### Post by leemgilbert on 2009-11-15
No one? :(

---

### Post by Fir3chi3f on 2009-11-15
I've been just getting this problem also, how large is the network that you are connected to? 

My school network is setup so that I usually see upwards of 60+ computers that I can connect to on that list. Sometimes I only see three and that is when I know that I will get the same error as you. It maybe the schools network prioritizing the service low.

What is your setup like? are you going through two routers?

---

### Post by froggger on 2009-11-15
this was the problem for me.
[http://www.sevenforums.com/tutorials/24232-sharing-permissions.html?filter](http://www.sevenforums.com/tutorials/24232-sharing-permissions.html?filter)[2]=Networking%20Internet

---

### Post by leemgilbert on 2009-11-15
No this is just a home network 2 Win 7 PC's and this Laptop running ubuntu 9.10.

I can connect by going to Places>Computer>CTRL-L then smb://192.168.2.5 (HTPC IP Address).

Not ideal, but at least I can see the drives now.

---

### Post by autonomy on 2009-11-15
I don't think this is a Samba problem or has anything to do with smb.conf. Looks like both computers are using the default Workgroup workgroup since you can see the Windows computer. I think you have to go into Windows and click the network icon beside the clock, and then, click Open Network and Sharing Center. I'm assuming these computers are at your home, so make sure your network is Home instead of Work or Public. If it's either of the latter, then just click on them and then click on Home network. Don't worry about the HomeGroup settings because that's just for other Windows 7 computers. 

Click on Change advanced sharing settings and turn on everything except for password protected sharing. A wireless router should help keep your Windows computer safe. Anyway, all you're opening up is the Public folder. When you're on Windows, you'll have to move the files to your desired folder. I have these settings turned on in the Public network, too, so go back and do that later if necessary. That may be all you need to do. Now, your Public folder (Computer -> C: -> Users -> Public) should be accessible from your Linux computer.

To make changes, you might need to go in that Users folder, right-click Public and click Properties, and then make sure Guest and Everyone have Read/Write permissions. You can click Advanced Sharing... on Public's Properties and make sure it's shared and that Everyone has Full Control. Having identical usernames on each computer helps especially when accessing the samba share on Linux. If necessary, click Places -> Connect to Server..., select Windows share, type in stimpy-htpc for the Server, check Add bookmark, type something like Windows 7 and click Connect. 

If this works and you have anymore questions about Samba or whatnot, just ask as I've learned a few other things.

---

### Post by leemgilbert on 2009-11-16
> **autonomy said:**
> I don't think this is a Samba problem or has anything to do with smb.conf. Looks like both computers are using the default Workgroup workgroup since you can see the Windows computer. I think you have to go into Windows and click the network icon beside the clock, and then, click Open Network and Sharing Center. I'm assuming these computers are at your home, so make sure your network is Home instead of Work or Public. If it's either of the latter, then just click on them and then click on Home network. Don't worry about the HomeGroup settings because that's just for other Windows 7 computers. 
 
Click on Change advanced sharing settings and turn on everything except for password protected sharing. A wireless router should help keep your Windows computer safe. Anyway, all you're opening up is the Public folder. When you're on Windows, you'll have to move the files to your desired folder. I have these settings turned on in the Public network, too, so go back and do that later if necessary. That may be all you need to do. Now, your Public folder (Computer -> C: -> Users -> Public) should be accessible from your Linux computer.
 
To make changes, you might need to go in that Users folder, right-click Public and click Properties, and then make sure Guest and Everyone have Read/Write permissions. You can click Advanced Sharing... on Public's Properties and make sure it's shared and that Everyone has Full Control. Having identical usernames on each computer helps especially when accessing the samba share on Linux. If necessary, click Places -> Connect to Server..., select Windows share, type in stimpy-htpc for the Server, check Add bookmark, type something like Windows 7 and click Connect. 
 
If this works and you have anymore questions about Samba or whatnot, just ask as I've learned a few other things.
 
Thank you for the suggestion.  As per my previous post I now have the drives mounted via SMB:\\ip addy.
 
They are permanently on my 'Computer', but I'm unable to rename these to something logical :(

---

### Post by dmizer on 2009-11-16
Please see the 6th link in my sig.

Edit:
Also, make sure that all firewalls are disabled.

---

