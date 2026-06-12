---
title: "sharing files - file permission nobody"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by elron on 2009-05-29
Hi,

I'm very very new to Ubuntu. So far my experience has been very positive and I'm enjoying it. 

I have reciently run into the following problem. I have searched extensively and it seems to be a common problem but the solution seems unclear to me.

The situation
I've setup a computer running ubuntu desktop 8 (with the latest updates) I've shared a folder and ubuntu downloaded and enabled filesharing. I've enabled guest access.
When I browse to this folder from my xp machine I can create files and delete them. When I attempt to do anything to them when I am on the ubuntu machine, it shows them as read only. When I look at them under properties => permission it shows owner as "nobody" and group as "nogroup".


Can anyone provide a step by step solution to this or point me to a guide? When I attempt to search the forums using the words with the word nobody in them, the search engine excludes the word "nobody" as being too common.

I would appreciate any help.

E

---

### Post by Danial on 2009-05-29
E,

To be honest, I am new (as compare to the gurus on this help forum) to Linux, however, I would suggest this article and I hope this may help you a bit regarding the windows share. No I have not installed the Samba on my system yet because I am going to re-install OS (9.04) on a new drive (later today) but once I am done with OS, I will be installing samba as I have a laptop with Vista to share files.  Here is the link:
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

I hope this will help you or give some directions.

Danial

---

### Post by Iowan on 2009-05-29
Post your */etc/samba/smb.conf*. If you set up shares from the desktop, they may be defined in a different place (which I gotta look up), but the  smb.conf file will reveal if your "nobody" is enabled.

---

### Post by elron on 2009-05-29
Thank you both for your reply.

Iowan, to get to the file you want to see I type in a terminal:

sudo /etc/samba/smb.conf

When I tried that I got "command not found" I'm doing something wrong I assume? However I was able to make my way to it manually from places.


Here it is below. Is the problem something to do with:

;   guest account = nobody

Do I need to remove the ";" I came across something to do with this while attempting to solve the problem myself.

Just to confirm that I did the right thing to enable sharing I did the following:

1. Created a folder in my home directory called test
2. right click => sharing
3. ubuntu wanted to download some files which it did
4. enabled sharing and ticked guests access as well as write access.


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
# "testparm" to check that you have not made any basic syntactic 
# errors. 
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

# Cap the size of the individual log files (in KiB).
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
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

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

# This option controls how nsuccessful authentication attempts are mapped 
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

---

### Post by munky99999 on 2009-05-29
Applicable guide is here.

[https://help.ubuntu.com/9.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/9.04/serverguide/C/samba-fileserver.html)

The thing is...

[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

Is good. Except. You also want to do this.

[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755
    force group = 
    force user = 

Then put whatever your user and group is.

Hell you generally dont have to do user. Usually just group should work.

---

### Post by elron on 2009-05-30
Ignore below....... searched and found I had to use the gedit command


Hmmmm, when I put in:
sudo /etc/samba/smb.conf

It gives me:
sudo: /etc/samba/smb.conf: command not found

I'm going applications ===> applications =======> Terminal to get a terminal up.

Am I doing something wrong here?

---

### Post by Iowan on 2009-05-30
*/etc/samba/smb.conf* is a configuration file - not an executable. You can view it with **cat**, **less**, **more**, or an editor like **gedit**, or (my preference) **nano**.

---

### Post by elron on 2009-05-30
I think I will have to admit defeat on this one at the moment. A BIG thank you to all the people who tried to help me. I have no programming background so it makes it a little hard.

It's unfortunate that when I share a directory under Ubuntu, people who save docs etc to that directiry with guest access end up making them read access to me. You would think there would be an easy fix to this but once again that may be my lack of knowledge.


Iowan,
I was very excited when I discovered the info you have posted below. It was a major step forward for me  :)

> **Iowan said:**
> */etc/samba/smb.conf* is a configuration file - not an executable. You can view it with **cat**, **less**, **more**, or an editor like **gedit**, or (my preference) **nano**.


Munky,

I followed the steps below and it worked after a fashon with the exception that the new shared directory created kept asking for a password. None of the passwords worked. In any case I just wanted a simple folder with guest access that stopped files being writted to it becoming "read only" to me.

> **munky99999 said:**
> Applicable guide is here.

[https://help.ubuntu.com/9.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/9.04/serverguide/C/samba-fileserver.html)

The thing is...

[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

Is good. Except. You also want to do this.

[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755
    force group = 
    force user = 

Then put whatever your user and group is.

Hell you generally dont have to do user. Usually just group should work.


Once again thank you to everyone.

El

---

### Post by rumplestilts on 2009-05-30
> **Iowan said:**
> */etc/samba/smb.conf* is a configuration file - not an executable. You can view it with **cat**, **less**, **more**, or an editor like **gedit**, or (my preference) **nano**.


So give him the proper command.

---

### Post by Iowan on 2009-05-30
> **rumplestilts said:**
> So give him the proper command.
Thought I did, but...
**cat /etc/samba/smb.conf**
**less /etc/samba/smb.conf**
**more /etc/samba/smb.conf**
**gksudo gedit  /etc/samba/smb.conf**
**sudo nano /etc/samba/smb.conf**

---

### Post by elron on 2009-05-30
Everything is fine. 

Iowan was expanding on my ignore post above. I discovered that I had to use an editor of some description after some research. That's why I went back and put an ignore header on my post that is three above. 

All good.

---

