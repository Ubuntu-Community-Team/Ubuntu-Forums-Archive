---
title: "Samba not accepting login creds"
date: 2012-09-03
forum: Networking &amp; Wireless
---

### Post by Mintnacho on 2012-09-03
Using 12.04 LTS The problem is I can see the shares thru nautilus and with smbclient commands.
When I try to access the shares from my other box I can see the shares but I can't access them as the username/password aren't being accepted. I don't get a prompt telling me why the login just comes back too me.

Users are added with the adduser command for the server itself and the smbpasswd for the samba user. Both accounts have the same passwords so password syncing isn't an issue.

I have 3 different users. 1 standard 1 admin with password and 1 admin w/o password. This happens on all 3.

Right now I'm using 2 linux distros. But I need samba for windows machines that will need to access the shares.
**Lastest Update**
So from the looks of it the smbusers might have been the issue. It now looks like I can access the share, but it wont mount. I get the following error
```
 'unable to mount location , failed to mount windows share' 
```

So anyone got anything on this? .. I've been googleing but haven't found my problem as of yet.


**first Update**
I've started fresh, I removed all smb packages with purge and hand deleted the left overs. I apt-get install samba and it installed for the most part. It didn't create /etc/samba .. but I had a backup. I also created the smb.conf which I've added below as well as a -d 3 on the one of the dirs. 

Someone in irc had mentioned the smbuser config. He brought up the question about mapping 3 different accounts to the same backend account 'administrator'

I'm not sure if this has anything to do with it.
****NEW smb.conf****
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
	workgroup = nekkednetwork

# server string is the equivalent of the NT Description field
	server string = entertainment

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
	dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
	name resolve order = bcast host lmhosts wins

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0
	interfaces = 192.168.1.0/24
# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
	bind interfaces only = yes



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
	security = user

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
#   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
#   passwd program = /usr/bin/passwd %u
#   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

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
# add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
# add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
# add group script = /usr/sbin/addgroup --force-badname %g

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
	username map = /etc/samba/smbusers
;	guest ok = no
;	guest account = nobody

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
#   usershare allow guests = no

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
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
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

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

[tv.series]
	comment = xv.tv
	path = /media/xblk.share/warez/tv.series
;	writeable = no
;	browseable = yes
	valid users = entbox, hfic0, hs

[xa.m1]
	comment = audio
	path = /media/xblk.share/warez/music
;	writeable = no
;	browseable = yes
	valid users = entbox, hfic0, hs

[xv.m1]
	path = /media/xblk.share/warez/movies
;	writeable = no
;	browseable = yes
	valid users = entbox, hfic0, hs

[xd.hbk1]
	comment = h.old.lp
	path = /media/xblk.share/move.it.off/holly_lp
	writeable = yes
;	browseable = yes
	valid users = hs

[xv.d1]
	comment = docus
	path = /media/xblk.share/warez/Documentary
;	writeable = no
;	browseable = yes
	valid users = entbox, hfic0

```

***d 3 on //ip/xa.m1 as entbox account***
```

entbox@boc1:/$ smbclient -d 3 //192.168.1.2/xa.m1 -Uentbox
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
interpret_interface: using netmask value 24 from config file on interface eth0
added interface eth0 ip=192.168.1.2 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 3.6.3).
Enter entbox's password: 
Connecting to 192.168.1.2 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x60898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
session setup failed: NT_STATUS_LOGON_FAILURE

```

***OLD smb.conf**
```
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options (perhaps too
# many!) most of which are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentry and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command "testparm"
# to check that you have not made any basic syntactic errors. 
#
#======================= Global Settings =====================================

[global]
	workgroup = nekkednetwork
	server string = entertainment
	hosts allow = 192.168.1.0/24 127.
	printcap name = /etc/printcap
	cups options = raw
	log file = /var/log/samba/%m.log
	max log size = 50
	security = user
	username map = /etc/samba/smbusers
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	name resolve order = wins lmhosts bcast
	dns proxy = no
	encrypt passwords = no
;	guest ok = no
;	guest account = nobody

[homes]
	comment = Home Directories
;	browseable = yes
	writable = yes
# Un-comment the following and create the netlogon directory for Domain Logons

; [netlogon]
;   comment = Network Logon Service
;   path = /home/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no
# Un-comment the following to provide a specific roving profile share
# the default is to use the user's home directory

;[Profiles]
;    path = /home/profiles
;    browseable = no
;    guest ok = yes
# NOTE: If you have a BSD-style print system there is no need to 
# specifically define each individual printer

[printers]
	comment = All Printers
	path = /var/spool/samba
	browseable = no
# Set public = yes to allow user 'guest account' to print
;	guest ok = no
;	writable = No
	printable = yes
# This one is useful for people to share files

;[tmp]
;   comment = Temporary file space
;   path = /tmp
;   read only = no
;   public = yes
# A publicly accessible directory, but read only, except for people in
# the "staff" group

;[public]
;   comment = Public Stuff
;   path = /home/samba
;   public = yes
;   read only = yes
;   write list = @staff
# Other examples. 
#
# A private printer, usable only by fred. Spool data will be placed in fred's
# home directory. Note that fred must have write access to the spool directory,
# wherever it is.

;[fredsprn]
;   comment = Fred's Printer
;   valid users = fred
;   path = /homes/fred
;   printer = freds_printer
;   public = no
;   writable = no
;   printable = yes
# A private directory, usable only by fred. Note that fred requires write
# access to the directory.

;[fredsdir]
;   comment = Fred's Service
;   path = /usr/somewhere/private
;   valid users = fred
;   public = no
;   writable = yes
;   printable = no
# a service which has a different directory for each machine that connects
# this allows you to tailor configurations to incoming machines. You could
# also use the %u option to tailor it by user name.
# The %m gets replaced with the machine name that is connecting.

;[pchome]
;  comment = PC Directories
;  path = /usr/pc/%m
;  public = no
;  writable = yes
# A publicly accessible directory, read/write to all users. Note that all files
# created in the directory by users will be owned by the default user, so
# any user with access can delete any other user's files. Obviously this
# directory must be writable by the default user. Another user could of course
# be specified, in which case all files would be owned by that user instead.

;[public]
;   path = /usr/somewhere/else/public
;   public = yes
;   only guest = yes
;   writable = yes
;   printable = no
# The following two entries demonstrate how to share a directory so that two
# users can place files there that will be owned by the specific users. In this
# setup, the directory should be writable by both users and should have the
# sticky bit set on it to prevent abuse. Obviously this could be extended to
# as many users as required.

;[myshare]
;   comment = Mary's and Fred's stuff
;   path = /usr/somewhere/shared
;   valid users = mary fred
;   public = no
;   writable = yes
;   printable = no
;   create mask = 0765

[xv.d1]
	comment = docu
	path = /media/xblk.share/warez/Documentary
;	writeable = no
;	browseable = yes
	valid users = entbox, hfic0, hfictst

[warez]
	path = /media/xblk.share/warez
	writeable = yes
;	browseable = yes
	valid users = entbox, hfic0, hfictst

[xbk.h1]
	comment = old.h.lp
	path = /media/xblk.share/move.it.off/holly_lp
	writeable = yes
;	browseable = yes
	valid users = hs

[xd.eb1]
	path = /media/xblk.share/warez/ebooks
	writeable = yes
;	browseable = yes
	valid users = entbox, hfic0

```

I'm also only talking about the following shares. The others are just garbage from the conf. I haven't removed yet.
```

[xv.d1]
	comment = docu
	path = /media/xblk.share/warez/Documentary
;	writeable = no
;	browseable = yes
	valid users = entbox, hfic0, hfictst

[warez]
	path = /media/xblk.share/warez
	writeable = yes
;	browseable = yes
	valid users = entbox, hfic0, hfictst

[xbk.h1]
	comment = old.h.lp
	path = /media/xblk.share/move.it.off/holly_lp
	writeable = yes
;	browseable = yes
	valid users = hs

[xd.eb1]
	path = /media/xblk.share/warez/ebooks
	writeable = yes
;	browseable = yes
	valid users = entbox, hfic0

```
smbusers
```
# Unix_name = SMB_Name1 SMB_Name2 ...
root = administrator
nobody = guest smbguest pcguest
entbox = administrator
test = user

hfic0 = administrator
hs = hs

```

The main folder for sharing is : 
drwxrwxrwx  5 entbox root    4096 Aug 29 22:58 xblk.share

/media/xblk.share/
drwx------ 12 entbox root        4096 Aug 29 23:04 move.it.off
drwxr----- 10 entbox sambashare  4096 Aug 29 15:23 warez

Now I don't have anyone in the sambashare group because I haven't setup groups or even started looking into setting up groups. 
This might be the way I would need to go, but without even being able to get a single user signed in .. groups might be a waste of time at this point as well.

I'm not the expert but I'm willing to try anything.

---

### Post by lievendp on 2012-09-03
Have you tried checking your samba logfiles on the server? It might hold some clues to why you're not getting loggedin from the other box.

Also, if you mount the cifs share on the other box or use smbclient, do you get any different errors/messages?

I wonder if your permissions (acl) on the server are set correctly, try creating a sambashare that is readable and writable for everybody.

Or maybe you're using something like selinux or apparmor that could deny access?

Another usefull tool in this is the tcpdump/wireshark so you can see exactly what the protocol is transferring. 

rgds,
Lieven

---

### Post by Mintnacho on 2012-09-03
This is what the log for the specific client I'm trying to connect
```

[2012/09/02 13:37:29.289000,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/xa.m1 failed. Permission denied
[2012/09/02 13:37:31.551683,  0] param/loadparm.c:9114(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/xa.m1 failed. Permission denied

```

Now I haven't been trying to access this share, .. but this seems to be a problem as well. 

I don't have anything specific installed to block access. This is a fresh install

I've also here is my fstab for the specific mount.Maybe a problem here?
```
 UUID=b4ffd79c-5f3d-4604-91ab-0ef3867f8e4b /media/xblk.share auto rw,auto,user,exec 0 0
```

---

### Post by Mintnacho on 2012-09-03
Solved!!

Ok so for anyone who has problems like this. I've manged to get it all working correctly. Besides 1 part, ..which for right now I dont care about. 

I do need to thank RiXtEr in #samba on freenode for pointing me in the right direction. Although RiXtEr didn't know if he was right he was dead on.

smbusers can't be mapped to the same names ie 'administrator'
smbusers maps login accounts to unix accounts for smb. 
As I figured out if client machine has 'hfic' and smb server has 'hfic0' then in the smbusers it must be 
hfic0 = hfic then login with the smbpassword.

Also and I haven't quite figured this part out. But it seems the issue was also sharing specific folders. 
I had /media/xblk.share/warez and under warez were other shares I was sharing out. I couldn't get to them. 
I removed the shares from /warez/ and put them directly into /media/xblk.share 
did addgroup group1 
chown -R root:group1 /xblk.share and chmod 775 /xblk.share 

I'm now accessing the shares just fine .. Having hiccups with the windows machine. But I believe that is just login based.

Hope this thread helps anyone else. I've spent the better part of 2days working on this issue. Multiple purges and new configs.

---

