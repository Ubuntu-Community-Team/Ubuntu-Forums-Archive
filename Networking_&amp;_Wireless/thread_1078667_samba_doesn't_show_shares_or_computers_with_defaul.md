---
title: "samba doesn't show shares or computers with default install"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by Mikywing on 2009-02-23
Hi all!! I have a very annoying problem with samba which i tried to resolve with many howtos, but without results. So this forum is my last try:D

I have a desktop PC and a notebook with Ubuntu 8.04 LTS on both, perfectly working. I also have another notebook which runs Windows XP SP3. I need all of them able to share files and printers, so i took a look at samba. I started it all trying to share a folder of the desktop PC (Ubuntu 8.04), then a wizard popped up: i followed all the steps, rebooted, and i thought samba was installed. I've done the same on the first notebook (Ubuntu 8.04). I've also set the Domain to "CASA" in both PC's under System->Administration->Network, shared some folders and then rebooted. After rebooting i've gone to Places->Network, which took manymany seconds to load (about 20-30 O.o) then double-clicked on "Windows-Network"... and found nothing!
Reading around the web, i realized that Ubuntu 8.04 doesn't change the samba domain through the System->Administration->Network tool, but through it's file /etc/samba/smb.conf. I changed the domain also in smb.conf, rebooted and again it shows nothing!


I tried to ping the PC's each other and it works.
Then, following some howtos, i thought that maybe i had to add some users to samba using the smbpasswd command. Done, but nothing changed.
I also tried the command "smbclient -L *somehosthere*" on the Desktop PC but it works only with the local hostname, not with the notebook's one (which is remote). In this last case, or if i type a wrong IP or hostname i get this output:
```
wingman@sandiego:~$ smbclient -L Lancaster
timeout connecting to 67.215.**.***:445
timeout connecting to 67.215.**.***:139
Error connecting to 67.215.**.*** (Operation already in progress)
Connection to Lancaster failed (Error NT_STATUS_ACCESS_DENIED)

```
But i've never heard that IP, and certainly it's not used by anyone of my PC's! O.o
If i use the command "smbclient -L *IP*" (so using IP's instead of hostnames) samba askes me for a password. I tried every password i know, even root's one but it doesn't accept anyone.

What's going wrong??:(

PS:
Here's my smb.conf (which is almost the default one, except for the domain)

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

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = CASA

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
```

---

### Post by cariboo on 2009-02-23
I would check to see if any of the computers have been assigned the same ip address. When using smbclient to check you shares, try this:

```
smbclient -L <server> -U%
```

Jim

---

### Post by Mikywing on 2009-02-24
Thankyou for the reply :)

Well, both Ubuntu pc's (since actually the Windows XP notebook isn't here with me) have different IP addresses: the Desktop has 192.168.1.101 and the notebook  192.168.1.100. The IP's can obviously change on every reboot because of DHCP, but i check them every time ;)

I tried the command you told me on both pc's using IP's (since hostnames doesn't work as i told you)
```
smbclient -L <serverip> -U%
```
And here's the output of Desktop PC (named sandiego)
```
wingman@sandiego:~$ smbclient -L 192.168.1.100 -U%
Domain=[CASA] OS=[Unix] Server=[Samba 3.0.28a]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (Lancaster server (Samba, Ubuntu))
	deskjet_5100    Printer   hp deskjet 5100
	video           Disk      
Domain=[CASA] OS=[Unix] Server=[Samba 3.0.28a]

	Server               Comment
	---------            -------
	LANCASTER            Lancaster server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	CASA                 

```
And here's the one from the notebook (named Lancaster)
```
alessandra@Lancaster:~$ smbclient -L 192.168.1.101 -U%
Domain=[CASA] OS=[Unix] Server=[Samba 3.0.28a]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (sandiego server (Samba, Ubuntu))
	deskjet_5100    Printer   hp deskjet 5100
	vecchio xp      Disk      
Domain=[CASA] OS=[Unix] Server=[Samba 3.0.28a]

	Server               Comment
	---------            -------
	SANDIEGO             sandiego server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	CASA                 

```

Thankyou again, i hope to find a solution :)

---

### Post by Faolan on 2009-02-24
Have you set up a share definition?

[ShareName]
path = /path to/share
browseable = yes
read only = no
guest ok = no
force user = username
force group = username group

This works for my shares and forces a log on.

You don't need to reboot your machine to restart Samba all you need to do is:

sudo /etc/init.d/samba restart

Also make sure your smb.conf is correct by running the testparm command.

---

### Post by Florida Cracker on 2009-02-24
Here is how I got mine to work:
I did a sudo gedit on my nsswitch.conf file and added wins in front of dns in the hosts:files line.
hosts:files ######## wins dns ####### (like this)
You also have to set the IP address in hosts tab in networking (through system/administration) for each machine you want to access. 
Here is a good video for setting up your samba configuration file. [http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)
I followed several howtos over the last several months and nothing worked until I put the wins in front of dns in the nsswitch.conf file.
Now all computers and shares show up and are mountable. If you are using DHCP, you will need to edit your hosts addresses when new IP's are assigned from time to time.

---

### Post by albinootje on 2009-02-24
> **Mikywing said:**
> 
Here's my smb.conf (which is almost the default one, except for the domain)

You have to add a share section if you want to share files.
Please read this :
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

And if that's too difficult or too time consuming, try webmin for a GUI style admin web interface.

---

