---
title: "Samba help"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by hosinfefer on 2011-03-05
I have a folder set up in samba call /nas

I have read\write to the folder /nas but if I want to add a file to say /nas/VM's I get permission denied.

This is on my local network so I dont care about passwords\usernames. I want full read\write from /nas and down. Can someone plz help me with this??

---

### Post by camorri on 2011-03-05
First thing to do is look at the directory permissions. Do that in at a terminal window. The command would be 'ls -dl /nas' If /nas is in the root as you indicate, who owns it? Then look at 'ls -dl /nas/VM' and see who owns it, and who has read/write permissions. Your user needs the correct read/write permissions, before you look at samba.

---

### Post by hosinfefer on 2011-03-05
Thx for the reply. I had to go back to work for a minute so I cant see that right now. I am coming from the windows world so I thought there might be a way to do a "everyone" access for both read\write from /nas/XX/XX/XX down.

I will get those ls's for you.

---

### Post by hosinfefer on 2011-03-06
graeme@graeme-sever:~$ cd /nas
graeme@graeme-sever:/nas$ ls -dl
drwxrwxrwx 15 graeme graeme 4096 2011-03-06 00:17 .
graeme@graeme-sever:/nas$ cd vm/
graeme@graeme-sever:/nas/vm$ ls -dl
drwxr-xr-x 5 graeme graeme 4096 2011-03-05 19:29 .
graeme@graeme-sever:/nas/vm$ 



so there is my problem...missing 2 w's for the user graeme. How can I force this extra rights from /nas down through all the folders in the /nas dir?

---

### Post by camorri on 2011-03-06
The command chmod will change the read/write/execute bits for a directory, as it will for a file. 

Example, 'chmod 664 directory' would set read/write/execute to read/write for user and group, and read only for other to the 'directory'. 

Once that is done, you may not be out of the woods yet, give it a try from a networked machine, there can still be problems in /etc/samba/smb.conf file. If there is, post the file.

---

### Post by hosinfefer on 2011-03-06
so i did the chmod 664 and then I could not even nav to the folder /nas on my server let alone a network computer. I did a sudo chmod 777 nas and I can now read\write to nas again from server and network computer. I have read\write to everything under the /nas still but not from a network pc

Here is samba file

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
	workgroup = workgroup
	netbios name = graeme-server

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
   security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
	encrypt passwords = false

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;	passdb backend = tdbsam

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

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes
	security = share
;	guest ok = no
;	guest account = nobody

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

#Graeme share
[nas]
	comment = nas
	path = /nas
	read only = no
	guest ok = yes
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
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[nas]
	path = /nas
	writeable = yes
;	browseable = yes
	guest ok = yes
	comment = NAS

---

### Post by camorri on 2011-03-06
> I have read\write to everything under the /nas still but not from a network pc


This is fine. You now have to look at the groups your users belong to. The root directory should not be 777 permissions. That allows anyone to read/write/execute. 

> ls -dl
drwxr-xr-x 5 graeme graeme 4096 2011-03-05 19:29

From this, graeme is the owner and group. Do your user(s) belong to the graeme group? If not, add them, and try again.

---

### Post by Morbius1 on 2011-03-06
You need to have /nas set at 777 because of your share definition:
> [nas]
    path = /nas
    writeable = yes
;    browseable = yes
[COLOR=Blue]     guest ok = yes[/COLOR]
    comment = NAS     "guest" in samba corresponds to "other" in linux so 777 is a must.

The reason you can't get write access to the VM subdirectory is because it too has the wrong permissions:
> graeme@graeme-sever:/nas/vm$ ls -dl
drwxr-xr-x 5 graeme graeme 4096 2011-03-05 19:29 .The remote guest can read and not write to the the vm subdirectory.

Rather than chmoding for the next 2 hours I may have a work around for all this. Change your share definition to add one line:
> [nas]
     path = /nas
     writeable = yes
 ;    browseable = yes
[COLOR=Blue]     [COLOR=Black]guest ok = yes[/COLOR][/COLOR]
[COLOR=Blue]**force user = graeme**[/COLOR]
     comment = NAS     The remote "guest" will be converted to "graeme" at lest for that share and graeme has access to everything.

Since you're in smb.conf anyway you might want to fix an error. Find the following line:

> encrypt passwords = falseThat should be set to true:
```
encrypt passwords = true
```Then restart samba:
```
sudo service smbd restart
```

---

### Post by hosinfefer on 2011-03-06
> Rather than chmoding for the next 2 hours I may have a work around for all this. Change your share definition to add one line:

This worked perfect. Thanks guys. Now my whole network has read\write to my 9TB nas. I was hoping there would be a quick fix and not have to go through my entire nas changing rights.

Thanks again guys!!!

---

