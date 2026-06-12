---
title: "Can't hide files from windows on samba share"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by technosinner on 2009-01-21
Hi,

This is take two of my question, as my first post went unanswered (my title wasn't very explicit...).

I am trying to get Samba - which otherwise works like a charm - to map the hidden flag for my Windows clients.  Currently, even if the option "map hidden = yes" is in my smb.conf, if I try to check 'hidden' in Windows Explorer the file/folder will not keep the attribute and when I re-open it, the check mark disappeared again.  This does not generate any orrer message, the check mark is functional, but disappears.

On the same share, I have the option to hide .files and that works fine, so I can't figure it out.  Also, if I go to Unix chmod and change it to 755 for instance, it will hide the file in Windows... Could this be caused by my default creation mask??

Surprisingly enough I can't locate any troubleshoot for this, so you're help will be greatly appreciated.

Thanks
ts

---

### Post by technosinner on 2009-01-21
My smb.conf is as follows.  The share I'm trying to get to work is in [homes].

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
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	socket options = TCP_NODELAY
	obey pam restrictions = yes
	map to guest = bad user
	encrypt passwords = true
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	dns proxy = no
	server string = The Crusade's Library
	invalid users = root
	unix password sync = yes
	workgroup = SINFUL_CRUSADE
	os level = 20
	security = user
	syslog = 0
	usershare allow guests = yes
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000
	pam password change = yes

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of

# server string is the equivalent of the NT Description field

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.

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

# Cap the size of the individual log files (in KiB).

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.

# Do something sensible when Samba crashes: mail the admin a backtrace


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  


;   guest account = nobody

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.

# This option controls how nsuccessful authentication attempts are mapped 
# to anonymous connections

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



#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
[homes]
        comment = Home Directories
	browseable = no
	map archive = yes
	writable = yes
	map hidden = yes
	hide dot files = yes
	valid users = %S

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


#======================= Library Shares =======================

[Audio]
	comment = Audio propaganda
	writeable = yes
	path = /Audio
        available = yes

[Backup]
	comment = Museum
	writable = yes
	path = /Backup
	available = yes

[Repository]
	comment = Repository
	writable = yes
	path = /Repository
	available = yes

[www]
	comment = WWW
	valid users = technosinner
	writeable = yes
	path = /var/www
        available = yes

[vault]
	comment = Vault
        valid users = technosinner
	writable = yes
	path = /home/vault
	available = yes
        browsable = no



[usbdrv]
	comment = USB
	writable = yes
	path = /media/usbdrv
	available = yes

```

---

### Post by Iowan on 2009-01-21
My Samba Unleashed book mentions that in addition to the *map hidden = true*, you need to "make sure *create mask=* is an odd number in the 1's place (*other*)."

---

### Post by bab1 on 2009-01-21
> **technosinner said:**
> Hi,

This is take two of my question, as my first post went unanswered (my title wasn't very explicit...).

I am trying to get Samba - which otherwise works like a charm - to map the hidden flag for my Windows clients.  


What type of Windows clients are you refering to?  The "map hidden = yes" is specifically for clients that use FAT32. These would be MS DOS, Windows 3.11, Win95/98.  If you are using Later Windows clients then, as Iowan has said: set the create mask to  something like 751.  This makes the file executable but not readable.  Heck, I would just make it 750 and then it just doesn't exist as far as others ar concerned.   

> Currently, even if the option "map hidden = yes" is in my smb.conf, if I try to check 'hidden' in Windows Explorer the file/folder will not keep the attribute and when I re-open it, the check mark disappeared again.  This does not generate any orrer message, the check mark is functional, but disappears.

For the same reasons as stated above.  It makes no sense to the OS.> 

On the same share, I have the option to hide .files and that works fine, so I can't figure it out.  Also, if I go to Unix chmod and change it to 755 for instance, it will hide the file in Windows... Could this be caused by my default creation mask??

Exactly.  If you look at the share files from the Linux server, none of the samba configs mean anything. > 

Surprisingly enough I can't locate any troubleshoot for this, so you're help will be greatly appreciated.


See:

[URL="http://oreilly.com/catalog/samba/chapter/ch05.html"][COLOR="Green"][B] File Permissions and Attributes on MS-DOS and Unix
[/B][/COLOR][/URL]
> 

Thanks
ts

---

### Post by dmizer on 2009-01-22
This is a file system problem, not a samba problem. Linux and Windows mark hidden files differently. If you want files to be hidden from Linux, you must prefix them with a dot like so:
```
.filename.exe
```

As an asside, I hope that your web server is not live to the world, because I assume you put 777 permissions on the /var/www folder so it could be changed over samba? If so, that means _anyone_ can make changes to your web directory from remote on the WWW. Here's how it happened to me: [http://ubuntuforums.org/showthread.php?t=688979](http://ubuntuforums.org/showthread.php?t=688979)

Secondly, I strongly recommend against sharing your entire home directory to Windows. A few clicks in Windows can render many things useless. Just make a dedicated share directory and share everything from there.

---

### Post by technosinner on 2009-01-22
Thank you for your guidance.  I did understand the problem was from the filesystem and not Samba, but I didn't realize that the mask had an impact on this.  I'll fiddle with these solutions and see what happens.

> **dmizer said:**
> As an asside, I hope that your web server is not live to the world, because I assume you put 777 permissions on the /var/www folder so it could be changed over samba? If so, that means _anyone_ can make changes to your web directory from remote on the WWW. Here's how it happened to me: [http://ubuntuforums.org/showthread.php?t=688979](http://ubuntuforums.org/showthread.php?t=688979)

Oh, don't worry!  My server is not accessible from the outside.  The /var/www/ is only an internal server.  I had read your post actually when I was setting up my server ;)

> **dmizer said:**
> Secondly, I strongly recommend against sharing your entire home directory to Windows. A few clicks in Windows can render many things useless. Just make a dedicated share directory and share everything from there.

I'm curious about what you meant..?  The reason I did it this way was so all the users on the network (not 1000 but still, a few) can get their shares without me having to create them individually.  As a matter or fact, the reason for this post here is because I'm trying to make some folders invisible to Windows but visible in Linux, thus I can't use the .Folder format.

Thanks!!

---

### Post by superprash2003 on 2009-01-22
try adding a $ to the end of the share name usually $ hides folders in windows.. so say sharename$

---

### Post by technosinner on 2009-01-22
Ah yes, but that work only on the share itself, not if I only want to hide a folder within it...

************

Good news!  I figured it out!  
Well in all honesty I didn't; I *read and understood* what you guys told me. See my mistake was that I thought I had my create mask properly set but when going through the .conf file again, I realized I had set up the defaults for new shares instead of the ones for the current ones...:oops:

So I added the line [FONT="Courier New"]create mask = 741[/FONT] in the .conf file under the currently active shares, and now I can manage the Hidden flags!

I feel really dumb for missing this, but it's a lot of details and I don't always see everything.
Also while sifting through the forums I found a similar post, which might be of use to anyone who stubles on this one: [http://ubuntuforums.org/showthread.php?t=127012](http://ubuntuforums.org/showthread.php?t=127012)

Thank you all for your help!
ts

---

### Post by dmizer on 2009-01-22
> **technosinner said:**
> I'm curious about what you meant..?  The reason I did it this way was so all the users on the network (not 1000 but still, a few) can get their shares without me having to create them individually.  As a matter or fact, the reason for this post here is because I'm trying to make some folders invisible to Windows but visible in Linux, thus I can't use the .Folder format.

Thanks!!

Just one small example: So if your Windows user make a change without understanding the consequences in Linux -> [http://ubuntuforums.org/showthread.php?t=899793](http://ubuntuforums.org/showthread.php?t=899793)

Sure, there are ways to prevent this, but you're still better off creating a new dedicated share for each individual. May be more effort for you in the short term, but it will probably be less effort (maintenance wise) for you in the long term.

---

### Post by technosinner on 2009-01-25
> **dmizer said:**
> Just one small example: So if your Windows user make a change without understanding the consequences in Linux -> [http://ubuntuforums.org/showthread.php?t=899793](http://ubuntuforums.org/showthread.php?t=899793)

Ah yeah I see.  Ok I'll try to work something out then.  Thanks for the advice!

---

