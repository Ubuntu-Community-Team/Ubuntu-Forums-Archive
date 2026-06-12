---
title: "Samba PDC / Windows profiles issue"
date: 2009-10-17
forum: Networking &amp; Wireless
---

### Post by Railbird on 2009-10-17
I hope this makes sense the way I'm asking it.... Thanks for any input!
 
Ok, so I have a home network setup. I'm using Kubuntu 9.04 with Samba 3.3.2 trying to create a domain named SPRINGFIELD
 
Everything actually works really well right now, but I have one strange thing going on:
 
The domain name is SPRINGFIELD
The host name of the PDC Domain server is APU
I am logging on as a user named JOEY
 
When I log into Windows on any of my workstations (Windows XP, Vista, and Windows 7) - the domain list on the logon screen shows the domain as SPRINGFIELD and JOEY can log in successfully.
 
However, if I detach any of the laptops from the network, I get the "Domain SPRINGFIELD is not available" error message. Which tells me that it wasn't caching the domain profile locally. HOWEVER -
 
If I change the username at the logon screen and log in as APU\Joey, it logs in and uses the same profile as if I had logged into the SPRINGFIELD domain. So somehow, it's storing the profile locally as APU\Joey instead of SPRINGFIELD\joey - so I can still log on to the laptop using a cached profile, but I have to change the username to APU\Joey
 
If you right-click on My computer, go to Properties -> Advanced -> User Profiles it shows APU\Joey as a user, and there is no SPRINGFIE:D\joey listed
 
SMB.CONF is below, I have given the output of the smbclient command first.....
 
Output of smbclient -L localhost -U anonymous%
----------------------------------------
smbclient -L localhost -U anonymous%
Domain=[SPRINGFIELD] OS=[Unix] Server=[Samba 3.3.2]
Sharename Type Comment
--------- ---- -------
print$ Disk Printer Drivers
IPC$ IPC IPC Service (Apu server (Samba, Ubuntu))
Domain=[SPRINGFIELD] OS=[Unix] Server=[Samba 3.3.2]
Server Comment
--------- -------
APU Apu server (Samba, Ubuntu)
BART
MAGGIE
Workgroup Master
--------- -------
SPRINGFIELD APU
 
-----------------------------------------------------------
 
smb.conf:
 
[global]
## Browsing/Identification ###
# Change this to the workgroup/NT-domain name your Samba server will part of
netbios name = APU
workgroup = SPRINGFIELD
os level = 64
preferred master = yes
# server string is the equivalent of the NT Description field
server string = %h server (Samba, Ubuntu)
# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
wins support = YES
# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
; wins server = w.x.y.z
# This will prevent nmbd to search for NetBIOS names through DNS.
dns proxy = no
# What naming service and in what order should we use to resolve host names
# to IP addresses
; name resolve order = lmhosts host wins bcast
#### Networking ####
# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
; interfaces = 127.0.0.0/8 eth0
# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself. However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
; bind interfaces only = yes
 
#### Debugging/Accounting ####
# This tells Samba to use a separate log file for each machine
# that connects
log file = /var/log/samba/log.%m
# Cap the size of the individual log files (in KiB).
max log size = 1000
# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
# syslog only = no
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
# You may wish to use password encryption. See the section on
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
# parameters must be set (thanks to Ian Kahan <<[EMAIL="kahan@informatik.tu-muenchen.de"]kahan@informatik.tu-muenchen.de[/EMAIL]> for
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
; logon path = [\\%N\profiles\%U]("file://\\%N\profiles\%U")
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
# logon path = [\\%N\%U\profile]("file://\\%N\%U\profile")
logon path =
logon home =
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
logon drive = U:
# logon home = [\\%N\%U]("file://\\%N\%U")
# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
; logon script = logon.cmd
# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe. The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe. 
# The following assumes a "machines" group exists on the system
add machine script = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe. 
; add group script = /usr/sbin/addgroup --force-badname %g
########## Printing ##########
# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
load printers = yes
# lpr(ng) printing. You may wish to override the location of the
# printcap file
; printing = bsd
; printcap name = /etc/printcap
# CUPS printing. See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
printing = cups
printcap name = cups
############ Misc ############
# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
; include = /home/samba/etc/smb.conf.%m
# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
# SO_RCVBUF=8192 SO_SNDBUF=8192
# socket options = TCP_NODELAY
# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
; message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
domain master = yes
# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
; idmap uid = 10000-20000
; idmap gid = 10000-20000
; template shell = /bin/bash
# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
; winbind enum groups = yes
; winbind enum users = yes
# Setup usershare options to enable non-root users to share folders
# with the net usershare command.
# Maximum number of usershare. 0 (default) means that usershare is disabled.
; usershare max shares = 100
# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
usershare allow guests = no
#======================= Share Definitions =======================
# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as [\\server\username]("file://\\server\username")
[homes]
comment = Home Directories
browseable = no
# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
read only = no
# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
create mask = 0775
# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
directory mask = 0775
# By default, [\\server\username]("file://\\server\username") shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to [\\server\username]("file://\\server\username")
# This might need tweaking when using external authentication schemes
valid users = %S
# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
; comment = Network Logon Service
; path = /home/samba/netlogon
; guest ok = yes
; read only = yes
; share modes = no
# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
; comment = Users profiles
; path = /home/samba/profiles
; guest ok = no
; browseable = no
; create mask = 0600
; directory mask = 0700
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

---

