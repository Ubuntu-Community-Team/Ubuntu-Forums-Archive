---
title: "Accessing Samba share issues"
date: 2013-06-08
forum: Networking &amp; Wireless
---

### Post by bcampbe81 on 2013-06-08
Hi All

So I am having some issues with winbind or at least something along those lines. I am trying to set up this PC to automatically load 3 different shares on startup. The three shares are located on 2 different devices on my home network. I have followed the following set of instructions

[https://help.ubuntu.com/community/MountWindowsSharesPermanently]("https://help.ubuntu.com/community/MountWindowsSharesPermanently")

and have since then followed the following as well

[http://ubuntuforums.org/showthread.php?t=1169149]("http://ubuntuforums.org/showthread.php?t=1169149")

I can connect to the shares if I navigate through my file explorer (thunar) and I can mount the drives if I use the IP address in the fstab file however I would rather be able to mount the drives using their netbios names. Unfortunately this is where I come to a bit of a hard spot as I have been going around and around in circles for the last few days to perform this and sitting spending much time on google to no avail.

My fstab file currently looks like this
```
//192.168.0.1/drive1 /media/Drive1 cifs guest,uid=1000,iocharset=utf8 0 0 
//192.168.0.1/drive3 /media/Drive3 cifs guest,uid=1000,iocharset=utf8 0 0
//192.168.0.7/drive2 /media/Drive2 cifs guest,uid=1000,iocharset=utf8 0 0
```

This DOES work however I would prefer to use the netbios name instead of the IP address

I have added the wins to the /etc/nsswitch.conf file and also installed winbind. I have added my netbios name to my /etc/samba/smb.conf file and ensured that all the devices are connected to the WORKGROUP workgroup with the same spelling to each device. If I change the IP address of the server to their respective netbios names I get the following.

```
bcampbe81@ManCave:~$ sudo mount -a
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

I'm at a loss of where to go from here and any help will be greatly appreciated.

Cheers 

Ben

---

### Post by bab1 on 2013-06-08
> **bcampbe81 said:**
> Hi All

So I am having some issues with winbind or at least something along those lines. I am trying to set up this PC to automatically load 3 different shares on startup. The three shares are located on 2 different devices on my home network. I have followed the following set of instructions

[https://help.ubuntu.com/community/MountWindowsSharesPermanently]("https://help.ubuntu.com/community/MountWindowsSharesPermanently")

and have since then followed the following as well

[http://ubuntuforums.org/showthread.php?t=1169149]("http://ubuntuforums.org/showthread.php?t=1169149")

I can connect to the shares if I navigate through my file explorer (thunar) and I can mount the drives if I use the IP address in the fstab file however I would rather be able to mount the drives using their netbios names. Unfortunately this is where I come to a bit of a hard spot as I have been going around and around in circles for the last few days to perform this and sitting spending much time on google to no avail.

My fstab file currently looks like this
```
//192.168.0.1/drive1 /media/Drive1 cifs guest,uid=1000,iocharset=utf8 0 0 
//192.168.0.1/drive3 /media/Drive3 cifs guest,uid=1000,iocharset=utf8 0 0
//192.168.0.7/drive2 /media/Drive2 cifs guest,uid=1000,iocharset=utf8 0 0
```

This DOES work however I would prefer to use the netbios name instead of the IP address

I have added the wins to the /etc/nsswitch.conf file and also installed winbind. I have added my netbios name to my /etc/samba/smb.conf file and ensured that all the devices are connected to the WORKGROUP workgroup with the same spelling to each device. If I change the IP address of the server to their respective netbios names I get the following.

```
bcampbe81@ManCave:~$ sudo mount -a
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

I'm at a loss of where to go from here and any help will be greatly appreciated.

Cheers 

Ben

Winbind is not used for WINS (netbios resolution).  Winbind is for mapping Windows users to Samba users in an NT Domain environment.  See [**[COLOR="#FF8C00"]here[/COLOR]**]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/winbind.html")for the Samba documentation on winbind.

You first step is to remove winbind and restore /etc/nsswitch.conf back to it's original format.

The server running smbd (the Samba daemon) should resolve the netbios names using nmbd ( the samba naming daemon).  From the client you are trying to mount the shares on, post the output of this command```
smbtree -d3
```

---

### Post by Morbius1 on 2013-06-08
@bab1, this is a completely inappropriate interruption in your thread but I was doing something for somebody yesterday and discovered something you might find interesting. 

They asked me to install wine. Never used it myself so I went to install it. By default it installs winbind. She didn't have a home network so Samba wasn't used and I didn't have a lot of time to see how or what it configured but it makes you wonder how many of the posts here with Samba issues are also from wine users.

---

### Post by bcampbe81 on 2013-06-08
@Morbius1 - Haven't installed wine on this PC. I have used it in the past but haven't gotten around to having a need for it on this PC just yet.

@bab1 - Thanks for the help, here is the output of smbtree -d3 after removing winbind and restoring my nsswitch.conf file.
```

benjamin@ManCave:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=fe80::21a:73ff:fe50:d704%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.0.2 bcast=192.168.0.255 netmask=255.255.255.0
Enter benjamin's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.1 ( 192.168.0.1 )
Connecting to host=192.168.0.1
Connecting to 192.168.0.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.0.1 ( 192.168.0.1 )
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.1 ( 192.168.0.1 )
Connecting to host=192.168.0.1
Connecting to 192.168.0.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.1 ( 192.168.0.1 )
Connecting to host=192.168.0.1
Connecting to 192.168.0.1 at port 445
Connecting to 192.168.0.1 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\REYTV          		WD TV Live
Connecting to host=REYTV
resolve_lmhosts: Attempting lmhosts lookup for name REYTV<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name REYTV<0x20>
resolve_wins: Attempting wins lookup for name REYTV<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name REYTV<0x20>
Got a positive name query response from 192.168.0.7 ( 192.168.0.7 )
Connecting to 192.168.0.7 at port 445
Server requested LANMAN password (share-level security) but 'client lanman auth = no' or 'client ntlmv2 auth = yes'
failed tcon_X with NT_STATUS_ACCESS_DENIED
	\\MANCAVE        		ManCave server
Connecting to host=MANCAVE
resolve_lmhosts: Attempting lmhosts lookup for name MANCAVE<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name MANCAVE<0x20>
resolve_wins: Attempting wins lookup for name MANCAVE<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name MANCAVE<0x20>
Got a positive name query response from 192.168.0.2 ( 192.168.0.2 )
Connecting to 192.168.0.2 at port 445
Connecting to 192.168.0.2 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\MANCAVE\benjamin       	Home Directories
		\\MANCAVE\Brother-HL-2130-series	Brother HL-2130 series
		\\MANCAVE\PDF            	PDF
		\\MANCAVE\IPC$           	IPC Service (ManCave server)
		\\MANCAVE\print$         	Printer Drivers
	\\LOUNBEN        		Lounben
Connecting to host=LOUNBEN
resolve_lmhosts: Attempting lmhosts lookup for name LOUNBEN<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name LOUNBEN<0x20>
resolve_wins: Attempting wins lookup for name LOUNBEN<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name LOUNBEN<0x20>
Got a positive name query response from 192.168.0.1 ( 192.168.0.1 )
Connecting to 192.168.0.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Pipe broken
anonymous failed session setup with NT_STATUS_IO_TIMEOUT
	\\BRW0080928F1628		
Connecting to host=BRW0080928F1628
resolve_lmhosts: Attempting lmhosts lookup for name BRW0080928F1628<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name BRW0080928F1628<0x20>
resolve_wins: Attempting wins lookup for name BRW0080928F1628<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name BRW0080928F1628<0x20>
Got a positive name query response from 192.168.0.9 ( 192.168.0.9 )
Connecting to 192.168.0.9 at port 445
Connecting to 192.168.0.9 at port 139
Error connecting to 192.168.0.9 (Connection refused)
cli_start_connection: failed to connect to BRW0080928F1628<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED

```

Don't really have time to go through it too much myself at the moment but will look more at it later.

Cheers for the help

Ben

---

### Post by bab1 on 2013-06-08
> **Morbius1 said:**
> @bab1, this is a completely inappropriate interruption in your thread but I was doing something for somebody yesterday and discovered something you might find interesting. 

They asked me to install wine. Never used it myself so I went to install it. By default it installs winbind. She didn't have a home network so Samba wasn't used and I didn't have a lot of time to see how or what it configured but it makes you wonder how many of the posts here with Samba issues are also from wine users.

Wow!  Another confusing question to ask newbies with Samba problems; "Did you install Wine at any time?"  A long time ago I found the first post that mentioned using winbind for WINS resolution.  I could shoot the guy!  But here we are some 6+ years down the road and still fighting the misunderstanding of what winbind is really for.

Thanks for the update.  I have never installed Wine on any machine so I would not have fount that.

The reason for winbind in Wine can  be found [**[COLOR="#FF8C00"]here[/COLOR]**]("http://wiki.winehq.org/NtlmAuthSetupGuide").  It's for authentication.  They just need the lib, not winbind itself.

---

### Post by bab1 on 2013-06-08
I see a few problems already (or at least the potential for problems).

Post the output of```
cat /etc/samba/smb.conf
```

What is the full hostname of ```
BRW0080928F1628
```

---

### Post by bcampbe81 on 2013-06-08
The 2 servers in really concerned about are the lounben and Reytv.  The ambiguous named share is my phone and any other pcs are not on all the time so yeah I'm really only intetested in getting those two shares working correctly as I very rarely access other machines on the network. The pc I'm attempting to Mount the shares on is named ManCave.

 post the out put of the cat command when I get home afternoon after I finish work

Cheers for the help

---

### Post by bcampbe81 on 2013-06-09
Output of cat /etc/samba/smb.conf

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
   netbios name = ManCave

# server string is the equivalent of the NT Description field
   server string = %h server

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
   name resolve order = lmhosts wins bcast host
;	name resolve order = bcast host

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

[homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# The following parameter makes sure that only "username" can connect
# to \\server\username
# This might need tweaking when using external authentication schemes
   valid users = %S

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

```

As for the device with the ambiguous name ... turns out it is the printer. A Brother HL-2135w to be exact.

---

### Post by bab1 on 2013-06-09
I am surprised at the output.  It appears that the hosts can be found (see below), but have trouble authenticating using *smbtree* which is unusual since you say you can mount the share using the IP address.  I assume you can manipulate the data too.  Maybe you didn't supply your password (anonymous)? ```
name_resolve_bcast: Attempting broadcast lookup for name REYTV<0x20>
Got a positive name query response from 192.168.0.7 ( 192.168.0.7 )
Connecting to 192.168.0.7 at port 445
Server requested LANMAN password (share-level security) but 'client lanman auth = no' or 'client ntlmv2 auth = yes'
failed tcon_X with NT_STATUS_ACCESS_DENIED

...

name_resolve_bcast: Attempting broadcast lookup for name LOUNBEN<0x20>
Got a positive name query response from 192.168.0.1 ( 192.168.0.1 )
Connecting to 192.168.0.1 at port 445
Doing spnego session setup (blob length=58)
...Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Pipe broken
anonymous failed session setup with NT_STATUS_IO_TIMEOUT
```

In the end the entire process chokes upon reaching this```
name_resolve_bcast: Attempting broadcast lookup for name BRW0080928F1628<0x20>
Got a positive name query response from 192.168.0.9 ( 192.168.0.9 )
Connecting to 192.168.0.9 at port 445
Connecting to 192.168.0.9 at port 139
Error connecting to 192.168.0.9 (Connection refused)
cli_start_connection: failed to connect to BRW0080928F1628<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
```

At this point I'm stumped.  What OS's are  REYTV and LOUNBEN running?  What are you using for local name services (IP resolution of LAN hosts)?

---

### Post by bcampbe81 on 2013-06-09
> **bab1 said:**
> I am surprised at the output.  It appears that the hosts can be found (see below), but have trouble authenticating using *smbtree* which is unusual since you say you can mount the share using the IP address.  I assume you can manipulate the data too.  Maybe you didn't supply your password (anonymous)? ```
name_resolve_bcast: Attempting broadcast lookup for name REYTV<0x20>
Got a positive name query response from 192.168.0.7 ( 192.168.0.7 )
Connecting to 192.168.0.7 at port 445
Server requested LANMAN password (share-level security) but 'client lanman auth = no' or 'client ntlmv2 auth = yes'
failed tcon_X with NT_STATUS_ACCESS_DENIED

...

name_resolve_bcast: Attempting broadcast lookup for name LOUNBEN<0x20>
Got a positive name query response from 192.168.0.1 ( 192.168.0.1 )
Connecting to 192.168.0.1 at port 445
Doing spnego session setup (blob length=58)
...Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Pipe broken
anonymous failed session setup with NT_STATUS_IO_TIMEOUT
```

In the end the entire process chokes upon reaching this```
name_resolve_bcast: Attempting broadcast lookup for name BRW0080928F1628<0x20>
Got a positive name query response from 192.168.0.9 ( 192.168.0.9 )
Connecting to 192.168.0.9 at port 445
Connecting to 192.168.0.9 at port 139
Error connecting to 192.168.0.9 (Connection refused)
cli_start_connection: failed to connect to BRW0080928F1628<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
```

At this point I'm stumped.  What OS's are  REYTV and LOUNBEN running?  What are you using for local name services (IP resolution of LAN hosts)?

Thanks for taking a look anyway. I'm reasonably stumped as well as it seems like everything should be working fine. 

LOUNBEN is my modem router working as a NAS (Netgear D6300). I can ping that and it works fine. The shares are set with guest access and as far as I am aware I cannot set users up for it although I haven't spent a lot of time fiddling with that as it is only new and haven't had a chance to do so yet. I can read and write to this fine using the mounts with the IP address in fstab or just through navigating through to either drive attached to the device.

REYTV is a WDTV Live Streaming media player. Once again set to guest access and has the ability to read/write to the drives.

Here is the fstab entries as they stand
```
//192.168.0.1/media /media/Media cifs guest,uid=1000,iocharset=utf8 0 0 
//192.168.0.1/media3 /media/Media3 cifs guest,uid=1000,iocharset=utf8 0 0
//192.168.0.7/media2 /media/Media2 cifs guest,uid=1000,iocharset=utf8 0 0
```

If I change the 192.168.0.1 and 192.168.0.7 in those three lines I get the following result
```
benjamin@ManCave:~$ sudo mount -a
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

The only change is changing the IP address to the netbios names. Rather frustrating... Any other thoughts?

Thanks in advance
Ben

---

### Post by bab1 on 2013-06-09
I'm going to guess here.  I think the problems are with the hosts REYTV and LOUNBEN.  These devices sometimes run an earlier version of Samba (v2) and have aspects that are not compatible with the version of Samba you are running on Ubuntu which is v3.6.  I think you should just live with what you have.

---

### Post by bcampbe81 on 2013-06-09
Yeah cheers. Thanks for the help. I'll just set the wd to static ipaddress as that was the only thing that will really change ip addresses and stuff up the system. That would have been the simple solution from the start but I just thought I might have been missing something

---

### Post by Morbius1 on 2013-06-10
If you have nothing else to do and want to try a "Hail Mary Pass" experiment bypass this netbios issue all together and access by mDNS ( host-name.local ) instead:
```
//lounben.local/media /media/Media cifs guest,uid=1000,iocharset=utf8 0 0 
//lounben.local/media3 /media/Media3 cifs guest,uid=1000,iocharset=utf8 0 0
//reytv.local/media2 /media/Media2 cifs guest,uid=1000,iocharset=utf8 0 0
```
[COLOR=#0000cd]*I'm not sure I associated the correct host name to the right ip address and I don't think it needs to be capitalized so you might want to check that.*[/COLOR]

It will only work if all of these devices speak avahi/bonjour/zeroconf/whatever-its-called. If they are supposed to support Apple products your chances may be good.

---

### Post by bcampbe81 on 2013-06-10
Cheers for the idea... not sure how that would work but I gave it a shot and got the following

```
mount error: could not resolve address for lounben.local: Unknown error
mount error: could not resolve address for lounben.local: Unknown error
mount error: could not resolve address for reytv.local: Unknown error
```

Cheers for the idea though... would you mind kind of explaining how that would work?

Ben

---

### Post by Morbius1 on 2013-06-10
Anything running avahi/bonjour can find and access each other with a hostname.local. All Apple products have this by default and as it turns out so do most Linux OS's. 

Wherever you do a hostname you can do a hostname.local. Like:

ping hostname.local
nautilus smb://hostname.local
nautilus ssh://hostname.local

But avahi/bonjour ( apple calls it bonjour ) must be running and it's ports must be open. It's a miracle really in an all Linux or a Linux/OSX/iOS network.

---

