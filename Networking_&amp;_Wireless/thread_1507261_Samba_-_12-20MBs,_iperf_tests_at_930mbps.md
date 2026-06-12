---
title: "Samba - 12-20MB/s, iperf tests at 930mbps"
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by talz13 on 2010-06-11
Subject says it all.  I can do an iperf test between my win7 desktop and my server at ~930mbps (116MB/s), but my usual throughput for samba shares is in the neighborhood of 12 to 20MB/s (or 96-160mbps).  Is there anything I can do to get this to sustain transfers more towards the 50MB/s area?

Server specs:
Ubuntu Server 9.04
Gigabyte EG43M-S2H
Intel E6300 2.8ghz dual core
4gb ddr2
4x 1TB WD black in raid 5 (home drive)
1x 640GB WD green (root / boot drive)

Desktop specs:
Win 7 Ult.
Gigabyte EP45-DS3L
Intel Q6600 2.4ghz quad core
4gb ddr2
2x 500GB WD (blue I think?)
Radeon HD5850

Network specs:
Netgear GS108 gigabit switch in server room
D-Link DGS-2208 (I think that's the model...) gigabit switch in desktop room
Cat6 cabling all around

I usually edit the samba config in webmin, so the main config section is near the top in the [global] settings.  The main tweaks for samba that I've found indicate playing with:
```
socket options = TCP_NODELAY SO_SNDBUF=65535 SO_RCVBUF=65535
```
My smb.conf on the server:
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
	log file = /var/log/samba/log.%m
	guest account = jeff
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	socket options = TCP_NODELAY SO_SNDBUF=65535 SO_RCVBUF=65535
	obey pam restrictions = yes
	map to guest = bad user
	encrypt passwords = true
	public = yes
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	dns proxy = no
	writeable = yes
	wide links = no
	delete readonly = yes
	server string = %h server (Samba, Ubuntu)
	unix password sync = yes
	workgroup = HOME
	os level = 20
	create mode = 660
	syslog = 0
	security = share
	guest only = yes
	usershare allow guests = yes
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000
	directory mode = 770
	pam password change = yes

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of

# server string is the equivalent of the NT Description field

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

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
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects

# Cap the size of the individual log files (in KiB).

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.

# Do something sensible when Samba crashes: mail the admin a backtrace


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  


# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.

# This option controls how unsuccessful authentication attempts are mapped 
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
;   create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0775

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




[apps]
	public = yes
	guest only = yes
	path = /home/shares/apps

[video]
	public = yes
	guest only = yes
	path = /home/shares/video

[music]
	copy = video
	path = /home/shares/music

[pictures]
	copy = video
	path = /home/shares/pictures

[games]
	copy = video
	path = /home/shares/games

[backup]
	copy = apps
	path = /home/shares/backup

[books]
	copy = video
	path = /home/shares/books
```

---

### Post by talz13 on 2010-06-13
How should I measure my disk performance on the server?  A simple hdparm -t /dev/md0 gave me a nice round number of ~330MB/s transfer rate (though I know real-world performance will not be THAT good), but at the least it should be more than enough to provide 50MB/s on large file transfers.  I don't care as much about random, small file performance since this is my media drive.  Most of the data on there consists of files between 3MB and 4GB.

---

### Post by talz13 on 2010-06-15
Nobody has any other ideas besides what I've tried already?  Any ideas how I should benchmark the read performance of my filesystem?

Does this topic need to be moved to the servers board?

---

### Post by jondavidf on 2010-06-15
I am not sure, but I am having a similar problem.  Both of my externals read at 120+ MB/sec but transfer at a max of 12 MB/sec.  All the gear I am running is Gigabit also.  I had the same equipment with Windows Server 2008 as the file server and got transfer rates of 60+ MB/sec.

---

### Post by mchlor on 2010-06-15
you might want to try tweaking your win7 box if you haven't already.

[http://www.speedguide.net/read_articles.php?id=2574](http://www.speedguide.net/read_articles.php?id=2574)

Also I dunno if it's fixed in win7 or not but playing something on windows media player will automatically throttle the network speed to max 12MB/sec on vista.

---

### Post by talz13 on 2010-06-16
> **mchlor said:**
> you might want to try tweaking your win7 box if you haven't already.

[http://www.speedguide.net/read_articles.php?id=2574](http://www.speedguide.net/read_articles.php?id=2574)

Also I dunno if it's fixed in win7 or not but playing something on windows media player will automatically throttle the network speed to max 12MB/sec on vista.

I hope it's not a bug like that.  Most of the time I do not have any kind of media player open (that I know of, at least).  It might be something to check into though.

---

### Post by jondavidf on 2010-06-16
Due to a power outage today all of my switches reset.  The server I have was on a backup UPS and didn't shut down.  Power came back up and voila, transfer rates jumped to 60MB/s.

Maybe one of your switches is transferring at 100 mbs instead of 1000

---

### Post by fearlsgroove on 2010-06-16
you can test raw disk performance with dd:

```
time dd if=/dev/zero of=/path/to/test/file/on/test/disk bs=64k count=1000
```

---

### Post by talz13 on 2010-06-16
> **fearlsgroove said:**
> you can test raw disk performance with dd:

```
time dd if=/dev/zero of=/path/to/test/file/on/test/disk bs=64k count=1000
```

Ok, I just ran that a few times (with 1000, 10000, and 100000 count, since 1000 completed so quickly), and got:```
jeff@server:~$ time dd if=/dev/zero of=/home/shares/video/test.dat bs=64k count=1000
1000+0 records in
1000+0 records out
65536000 bytes (66 MB) copied, 0.078237 s, 838 MB/s

real    0m0.081s
user    0m0.000s
sys     0m0.080s
jeff@server:~$ rm /home/shares/video/test.dat
jeff@server:~$ time dd if=/dev/zero of=/home/shares/video/test.dat bs=64k count=10000
10000+0 records in
10000+0 records out
655360000 bytes (655 MB) copied, 3.7889 s, 173 MB/s

real    0m3.794s
user    0m0.010s
sys     0m1.040s
jeff@server:~$ rm /home/shares/video/test.dat
jeff@server:~$ time dd if=/dev/zero of=/home/shares/video/test.dat bs=64k count=100000
100000+0 records in
100000+0 records out
6553600000 bytes (6.6 GB) copied, 91.0415 s, 72.0 MB/s

real    1m31.161s
user    0m0.010s
sys     0m11.820s
```

Disk speed looks fine to me.

> **jondavidf said:**
>  Due to a power outage today all of my switches reset. The server I have was on a backup UPS and didn't shut down. Power came back up and voila, transfer rates jumped to 60MB/s.

Maybe one of your switches is transferring at 100 mbs instead of 1000
I will check that out today, but if that were the case I believe iperf should be reporting 100mbps speeds as well.  My parents PC for some reason will not connect at gigabit speeds, but that's a problem for a different day.

---

### Post by jondavidf on 2010-06-17
You could try testing the network speed itself by transferring files between two Windows PC's to see what your speeds are.  Then you would know for sure if Samba is the culprit or if your network/interface is the issue.

---

### Post by talz13 on 2010-06-17
> **jondavidf said:**
> You could try testing the network speed itself by transferring files between two Windows PC's to see what your speeds are.  Then you would know for sure if Samba is the culprit or if your network/interface is the issue.

Shouldn't iperf be testing just that?  I know that my desktop gets ~900Mbps to the server, and my media pc (the only other windows pc I have) gets ~650Mbps to the server using iperf.

---

### Post by talz13 on 2010-07-27
I was just copying a lot of data back from my server to my parents' ubuntu PC via NFS and was VERY impressed!  I had sustained transfers of over 100 megabytes per second (800+mbps).  It's going to finish copying 209.5GB in ~33 minutes.  Maybe I should switch my media PC to ubuntu and take advantage of the awesome throughput of NFS mounted drives...

---

