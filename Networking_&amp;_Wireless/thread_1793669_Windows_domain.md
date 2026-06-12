---
title: "Windows domain"
date: 2011-06-29
forum: Networking &amp; Wireless
---

### Post by jenerics5 on 2011-06-29
I am trying to setup a server act as a Windows domain controller for my house and the 5 or som machines I connect to the network. I currently manage a Windows network and am very comfortable with the Windows configuration and how to install a Domain that way. 
 
I am trying to stay legal and save money by using SAMBA. I have followed the directions as best as I can follow from here, [https://help.ubuntu.com/11.04/serverguide/C/samba-dc.html](https://help.ubuntu.com/11.04/serverguide/C/samba-dc.html)
but I am not able to join a Windows XP computer to the domain. I have installed DHCP and DNS on the server and it seems to be working just fine. I am able to resolve the server name and the domain name and the computers are getting IP addresses.
 
The XP machine is gives and error that the domain controller for the domain cannot be found. The log says something about a service record DNS entry for the domain, but I do not know how to add that type of record. 
 
I am able to browse the network and see a couple of shares that I setup so I know the server is running and some the of the smb.conf file is set right. Below is a copy of what I have. Thanks for any help.
 
Eric
 
[FONT=Courier New][SIZE=3]#[/SIZE][/FONT]
[SIZE=3][FONT=Courier New]# Sample configuration file for the Samba suite for Debian GNU/Linux.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]#[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]#[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# This is the main Samba configuration file. You should read the[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# smb.conf(5) manual page in order to understand the options listed[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# here. Samba has a huge number of configurable options most of which [/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# are not shown in this example[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]#[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# Some options that are often worth tuning have been included as[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# commented-out examples in this file.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# - When such options are commented with ";", the proposed setting[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# differs from the default Samba behaviour[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# - When commented with "#", the proposed setting is the default[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# behaviour of Samba but the option is considered important[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# enough to be mentioned here[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]#[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# NOTE: Whenever you modify this file you should run the command[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# "testparm" to check that you have not made any basic syntactic [/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# errors. [/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# A well-established practice is to name the original file[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# "smb.conf.master" and create the "real" config file with[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# testparm -s smb.conf.master >smb.conf[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# This minimizes the size of the really used smb.conf file[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# which, according to the Samba Team, impacts performance[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# However, use this with caution if your smb.conf file contains nested[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# "include" statements. See Debian bug #483187 for a case[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# where using a master file is not a good idea.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]#[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]#======================= Global Settings =======================[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New][global][/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]## Browsing/Identification ###[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# Change this to the workgroup/NT-domain name your Samba server will part of[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]workgroup = JENERICS[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# server string is the equivalent of the NT Description field[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]server string = %h server (Samba, Ubuntu)[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# Windows Internet Name Serving Support Section:[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# WINS Support - Tells the NMBD component of Samba to enable its WINS Server[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# wins support = no[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# WINS Server - Tells the NMBD components of Samba to be a WINS Client[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; wins server = w.x.y.z[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# This will prevent nmbd to search for NetBIOS names through DNS.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]dns proxy = no[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# What naming service and in what order should we use to resolve host names[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# to IP addresses[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]name resolve order = lmhosts host wins bcast[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]#### Networking ####[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# The specific set of interfaces / networks to bind to[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# This can be either the interface name or an IP address/netmask;[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# interface names are normally preferred[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]interfaces = 127.0.0.0/16 eth0[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# Only bind to the named interfaces and/or networks; you must use the[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# 'interfaces' option above to use this.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# It is recommended that you enable this feature if your Samba machine is[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# not protected by a firewall or is a firewall itself. However, this[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# option cannot handle dynamic or non-broadcast interfaces correctly.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]bind interfaces only = yes[/FONT][/SIZE]
 
 
 
[SIZE=3][FONT=Courier New]#### Debugging/Accounting ####[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# This tells Samba to use a separate log file for each machine[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# that connects[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]log file = /var/log/samba/log.%m[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# Cap the size of the individual log files (in KiB).[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]max log size = 1000[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# If you want Samba to only log through syslog then set the following[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# parameter to 'yes'.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]syslog only = yes[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# We want Samba to log a minimum amount of information to syslog. Everything[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# through syslog you should set the following parameter to something higher.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]syslog = 10[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# Do something sensible when Samba crashes: mail the admin a backtrace[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]panic action = /usr/share/samba/panic-action %d[/FONT][/SIZE]
 
 
[SIZE=3][FONT=Courier New]####### Authentication #######[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# "security = user" is always a good idea. This will require a Unix account[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# in this server for every user accessing the server. See[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# in the samba-doc package for details.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]security = user[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# You may wish to use password encryption. See the section on[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# 'encrypt passwords' in the smb.conf(5) manpage before enabling.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]encrypt passwords = true[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# If you are using encrypted passwords, Samba will need to know what[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# password database type you are using. [/FONT][/SIZE]
[SIZE=3][FONT=Courier New]passdb backend = tdbsam[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]obey pam restrictions = yes[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# This boolean parameter controls whether Samba attempts to sync the Unix[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# password with the SMB password when the encrypted SMB password in the[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# passdb is changed.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]unix password sync = yes[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# For Unix password sync to work on a Debian GNU/Linux system, the following[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# sending the correct chat script for the passwd program in Debian Sarge).[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]passwd program = /usr/bin/passwd %u[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# This boolean controls whether PAM will be used for password changes[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# when requested by an SMB client instead of the program listed in[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# 'passwd program'. The default is 'no'.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]pam password change = yes[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# This option controls how unsuccessful authentication attempts are mapped[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# to anonymous connections[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]map to guest = bad user[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]########## Domains ###########[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# Is this machine able to authenticate users. Both PDC and BDC[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# must have this setting enabled. If you are the BDC you must[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# change the 'domain master' setting to no[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]#[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]domain logons = yes[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]#[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# The following setting only takes effect if 'domain logons' is set[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# It specifies the location of the user's profile directory[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# from the client point of view)[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# The following required a [profiles] share to be setup on the[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# samba server (see below)[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# logon path = \\%N\profile\%U[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# Another common choice is storing the profile in the user's home directory[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# (this is Samba's default)[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]logon path = \\%N\%U\profile[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# The following setting only takes effect if 'domain logons' is set[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# It specifies the location of a user's home directory (from the client[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# point of view)[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]logon drive = H:[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]logon home = \\%N\%U[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# The following setting only takes effect if 'domain logons' is set[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# It specifies the script to run during logon. The script must be stored[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# in the [netlogon] share[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# NOTE: Must be store in 'DOS' file format convention[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]logon script = logon.cmd[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# This allows Unix users to be created on the domain controller via the SAMR[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# RPC pipe. The example command creates a user account with a disabled Unix[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# password; please adapt to your needs[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# This allows machine accounts to be created on the domain controller via the [/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# SAMR RPC pipe. [/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# The following assumes a "machines" group exists on the system[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]add machine script = /usr/sbin/useradd -N -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# This allows Unix groups to be created on the domain controller via the SAMR[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# RPC pipe. [/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; add group script = /usr/sbin/addgroup --force-badname %g[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]########## Printing ##########[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# If you want to automatically load your printer list rather[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# than setting them up individually then you'll need this[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# load printers = yes[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# lpr(ng) printing. You may wish to override the location of the[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# printcap file[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; printing = bsd[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; printcap name = /etc/printcap[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# CUPS printing. See also the cupsaddsmb(8) manpage in the[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# cupsys-client package.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; printing = cups[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; printcap name = cups[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]############ Misc ############[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# Using the following line enables you to customise your configuration[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# on a per machine basis. The %m gets replaced with the netbios name[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# of the machine that is connecting[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; include = /home/samba/etc/smb.conf.%m[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# Most people will find that this option gives better performance.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# for details[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# You may want to add the following on a Linux system:[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# SO_RCVBUF=8192 SO_SNDBUF=8192[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# socket options = TCP_NODELAY[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# The following parameter is useful only if you have the linpopup package[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# installed. The samba maintainer and the linpopup maintainer are[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# working to ease installation and configuration of linpopup and samba.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# Domain Master specifies Samba to be the Domain Master Browser. If this[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# machine will be configured as a BDC (a secondary logon server), you[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# must set this to 'no'; otherwise, the default behavior is recommended.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]domain master = auto[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# Some defaults for winbind (make sure you're not using the ranges[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# for something else.)[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; idmap uid = 10000-20000[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; idmap gid = 10000-20000[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; template shell = /bin/bash[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# The following was the default behaviour in sarge,[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# but samba upstream reverted the default because it might induce[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# performance issues in large organizations.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# See Debian bug #368251 for some of the consequences of *not*[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# having this setting and smb.conf(5) for details.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; winbind enum groups = yes[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; winbind enum users = yes[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# Setup usershare options to enable non-root users to share folders[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# with the net usershare command.[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# Maximum number of usershare. 0 (default) means that usershare is disabled.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; usershare max shares = 100[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# Allow users who've been granted usershare privileges to create[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# public shares, not just authenticated ones[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]usershare allow guests = yes[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]#======================= Share Definitions =======================[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# Un-comment the following (and tweak the other settings below to suit)[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# to enable the default home directory shares. This will share each [/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# user's home director as \\server\username[/FONT][/SIZE]
[SIZE=3][FONT=Courier New][homes][/FONT][/SIZE]
[SIZE=3][FONT=Courier New]comment = Home Directories[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]browseable = no[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# By default, the home directories are exported read-only. Change the[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# next parameter to 'no' if you want to be able to write to them.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]read only = no[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# File creation mask is set to 0700 for security reasons. If you want to[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# create files with group=rw permissions, set next parameter to 0775.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]create mask = 0700[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# Directory creation mask is set to 0700 for security reasons. If you want to[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# create dirs. with group=rw permissions, set next parameter to 0775.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]directory mask = 0700[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# By default, \\server\username shares can be connected to by anyone[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# with access to the samba server. Un-comment the following parameter[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# to make sure that only "username" can connect to \\server\username[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# The following parameter makes sure that only "username" can connect[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]#[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# This might need tweaking when using external authentication schemes[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]valid users = %S[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# Un-comment the following and create the netlogon directory for Domain Logons[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# (you need to configure Samba to act as a domain controller too.)[/FONT][/SIZE]
[SIZE=3][FONT=Courier New][netlogon][/FONT][/SIZE]
[SIZE=3][FONT=Courier New]comment = Network Logon Service[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]path = /srv/samba/netlogon[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]guest ok = yes[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]read only = yes[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]share modes = no[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# This is a share added for music sharing on the Jenerics workgroup[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# for all of the computers. This was created 6-24-11 at 11:05 am.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New][music][/FONT][/SIZE]
[SIZE=3][FONT=Courier New]comment = Music Share[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]path = /share/music[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]guest ok = yes[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]read only = no[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]share modes = no[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# This is a share creted for the Stewart family pictures to be shared[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# on the network. Date created 6-24-11 at 11:16 am.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New][pics][/FONT][/SIZE]
[SIZE=3][FONT=Courier New]comment = Pictures Share[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]path = /share/pictures[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]guest ok = yes[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]read only = no[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]share modes = no[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# Un-comment the following and create the profiles directory to store[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# users profiles (see the "logon path" option above)[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# (you need to configure Samba to act as a domain controller too.)[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# The path below should be writable by all users so that their[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# profile directory may be created the first time they log on[/FONT][/SIZE]
[SIZE=3][FONT=Courier New][profiles][/FONT][/SIZE]
[SIZE=3][FONT=Courier New]comment = Users profiles[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]path = /home/samba/profiles[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]guest ok = no[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]browseable = no[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]create mask = 0600[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]directory mask = 0700[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New][printers][/FONT][/SIZE]
[SIZE=3][FONT=Courier New]comment = All Printers[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]browseable = no[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]path = /var/spool/samba[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]printable = yes[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]guest ok = no[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]read only = yes[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]create mask = 0700[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# Windows clients look for this share name as a source of downloadable[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# printer drivers[/FONT][/SIZE]
[SIZE=3][FONT=Courier New][print$][/FONT][/SIZE]
[SIZE=3][FONT=Courier New]comment = Printer Drivers[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]path = /var/lib/samba/printers[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]browseable = yes[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]read only = yes[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]guest ok = no[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# Uncomment to allow remote administration of Windows print drivers.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# You may need to replace 'lpadmin' with the name of the group your[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# admin users are members of.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# Please note that you also need to set appropriate Unix permissions[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# to the drivers directory for these users to have write rights in it[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; write list = root, @lpadmin[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# A sample share for sharing your CD-ROM with others.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New];[cdrom][/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; comment = Samba server's CD-ROM[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; read only = yes[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; locking = no[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; path = /cdrom[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; guest ok = yes[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]# The next two parameters show how to auto-mount a CD-ROM when the[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# cdrom share is accesed. For this to work /etc/fstab must contain[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# an entry like this:[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]#[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# /dev/scd0 /cdrom iso9660 defaults,noauto,ro,user 0 0[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]#[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# The CD-ROM gets unmounted automatically after the connection to the[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]#[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# If you don't want to use auto-mounting/unmounting make sure the CD[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]# is mounted on /cdrom[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]#[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; preexec = /bin/mount /cdrom[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]; postexec = /bin/umount /cdrom[/FONT][/SIZE]

---

### Post by helgman on 2011-06-30
> **jenerics5 said:**
> The XP machine is gives and error that the domain controller for the domain cannot be found. The log says something about a service record DNS entry for the domain, but I do not know how to add that type of record.

Microsoft use some special DNS records in their AD environment. This article, [http://technet.microsoft.com/en-us/library/dd316373.aspx](http://technet.microsoft.com/en-us/library/dd316373.aspx), might hold some clues as to what you need.

If not, try to Google something like "microsoft service records dns bind".

Regards,
Helgman

---

