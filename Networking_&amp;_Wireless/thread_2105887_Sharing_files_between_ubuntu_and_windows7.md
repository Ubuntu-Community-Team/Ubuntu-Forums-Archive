---
title: "Sharing files between ubuntu and windows7"
date: 2013-01-17
forum: Networking &amp; Wireless
---

### Post by Raafat1991 on 2013-01-17
Hi everyone.....

i followed this guide [http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/)

for sharing files between ubuntu 12.04 LTS and windows7 .

my problem is : ubuntu can see windows7 but the latter can't see ubuntu .


thanks....

---

### Post by Petro Dawg on 2013-01-17
I just use Ubuntu1 to share files between my Ubuntu and Win7 partitions as well as various computers (in my home and across the country) as well as my phone.  

Its rather easy to set up and works well.

Others prefer DropBox, either is fine for simply sharing files between computers.

---

### Post by irv on 2013-01-17
I agree. Ubuntuone is a great way to share files. A couple of weeks ago I purchased a Pogoplug for $20, and it really works great for sharing files over a LAN or the Internet. If you have any external Hard Drives laying around you can use them on your network. Here is a link to the [pogoplug]("http://www.amazon.com/gp/product/B005FNDJHS/ref=oh_details_o00_s00_i00").

---

### Post by Raafat1991 on 2013-01-18
Hi...there is no problem with your suggestions ( i will rember them later ) but i want to share files between ubuntu 12.04 LTS and windows7 directly (as with samba , but you know what is my problem )....thank you .

---

### Post by dannyboy79 on 2013-01-18
can you post your ubuntu /etc/samba/smb.conf file please. that guide seems very straight forward, what step can't you achieve? what's the error?

---

### Post by irv on 2013-01-18
I read the comments from your link: [http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/]("http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/") and one of the comments was that the poster of the howto did not use root permission to save the samba config file.
Also I want to mention that Windows can not read Ext4 partition so if you have files you want to share with windows they need to be keep on Fat43 or NTFS partitions.

---

### Post by dannyboy79 on 2013-01-18
> **irv said:**
> I read the comments from your link: [http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/]("http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/") and one of the comments was that the poster of the howto did not use root permission to save the samba config file.
Also I want to mention that Windows can not read Ext4 partition so if you have files you want to share with windows they need to be keep on Fat43 or NTFS partitions.the filesystem doesn't matter when sharing over samba, which is what he's trying to accomplish.

---

### Post by irv on 2013-01-18
> **dannyboy79 said:**
> the filesystem doesn't matter when sharing over samba, which is what he's trying to accomplish.

I guess I didn't know that because I don't use windows any more. I wonder if there is something like Airdroid so one could share files in a browser between Windows, Ubuntu (or any other Linux) including  Android?

---

### Post by dpurgert on 2013-01-18
is the windows user in the samba users list on the ubuntu machine?

---

### Post by lisanels47 on 2013-01-18
I just got this going the other day.  Here's my smb.conf file.  I didn't have to install anything on Ubuntu other than samba.  I put bold around the things I had to change.  Now the windows 7 system could browse the stuff I have shared etc.

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here.
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
[B]	workgroup = WORKGROUP
[/B]#   workgroup = HOME

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
[B]   name resolve order = bcast 
netbios name = LisaLaptop[/B]

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
;	encrypt passwords = yes

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
	**map to guest = bad user**

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
	username map = /etc/samba/smbusers
	security = user
	guest ok = yes
;	guest account = nobody
	guest account = nobody

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

[tmp]
	comment = Temp
	path = /tmp
	writeable = yes
;	browseable = yes
	guest ok = yes

---

### Post by Morbius1 on 2013-01-19
>  my problem is : ubuntu can see windows7 but the latter can't see ubuntu .Can Ubuntu see itself? Run the following command and post the output please:
```
smbtree
```And just to make sure, see if nmbd is running:
```
sudo service nmbd status
```If it's not running start it:
```
sudo service nmbd start
```If you have to start it wait about 5 minutes and then see if you can see it.

---

### Post by Raafat1991 on 2013-01-19
> **lisanels47 said:**
> I just got this going the other day.  Here's my smb.conf file.  I didn't have to install anything on Ubuntu other than samba.  I put bold around the things I had to change.  Now the windows 7 system could browse the stuff I have shared etc.

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here.
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
[B]    workgroup = WORKGROUP
[/B]#   workgroup = HOME

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
[B]   name resolve order = bcast 
netbios name = LisaLaptop[/B]

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
;    encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;    passdb backend = tdbsam

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
    **map to guest = bad user**

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
;    printing = cups
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
;    usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes
    username map = /etc/samba/smbusers
    security = user
    guest ok = yes
;    guest account = nobody
    guest account = nobody

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
;    guest ok = no
;    read only = yes
    create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
;    read only = yes
;    guest ok = no
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

[tmp]
    comment = Temp
    path = /tmp
    writeable = yes
;    browseable = yes
    guest ok = yes

Also no luck...

---

### Post by Raafat1991 on 2013-01-19
> **Morbius1 said:**
> Can Ubuntu see itself? Run the following command and post the output please:
```
smbtree
```And just to make sure, see if nmbd is running:
```
sudo service nmbd status
```If it's not running start it:
```
sudo service nmbd start
```If you have to start it wait about 5 minutes and then see if you can see it.

I did't find my computer of smbtree 

and nmbd is running.....

---

### Post by Morbius1 on 2013-01-19
Turn off your firewall and try smbtree again:
```
sudo ufw disable
```

[COLOR=Blue]**EDIT**[/COLOR]: Is Samba itself working? On your Ubuntu machine access yourself by ip address:
```
 nautilus smb://192.168.0.100
```
[COLOR=Blue]*Change 192.168.0.100 to your own ip address.*[/COLOR]

---

### Post by Raafat1991 on 2013-01-23
> **Morbius1 said:**
> Turn off your firewall and try smbtree again:
```
sudo ufw disable
```[COLOR=Blue]**EDIT**[/COLOR]: Is Samba itself working? On your Ubuntu machine access yourself by ip address:
```
 nautilus smb://192.168.0.100
```[COLOR=Blue]*Change 192.168.0.100 to your own ip address.*[/COLOR]

Yes i can access  ```
smb://myIP
```

---

### Post by Morbius1 on 2013-01-23
You know you never did what **[COLOR=Blue]dannyboy79[/COLOR]** suggested a few days/weeks ago so why not post the output of the following commands:
```
testparm -s
``````
smbtree
``````
hostname
```I added a few others in there ;)

---

### Post by Raafat1991 on 2013-01-25
> **Morbius1 said:**
> You know you never did what **[COLOR=Blue]dannyboy79[/COLOR]** suggested a few days/weeks ago so why not post the output of the following commands:
```
testparm -s
``````
smbtree
``````
hostname
```I added a few others in there ;)


```
testparm -s
```its ouput :

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[myBooks]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = UBUNTU
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    name resolve order = bcast
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[myBooks]
    path = /home/raafat/Desktop/For_me/temp/myBooks
    read only = No
    guest ok = Yes

```


```
smbtree
```
its output :

```
WORKGROUP
    \\PPT-20121118VXO        
UBUNTU
    \\CENTER_INFO            Center_info
        \\CENTER_INFO\Users              
        \\CENTER_INFO\print$             Printer Drivers
        \\CENTER_INFO\IPC$               Remote IPC
        \\CENTER_INFO\HP Color LaserJet CP1510 series PCL6    HP Color LaserJet CP1510 series PCL6
        \\CENTER_INFO\D$                 Default share
        \\CENTER_INFO\C$                 Default share
        \\CENTER_INFO\ADMIN$             Remote Admin
RABWAH
    \\WESAM                  
    \\SER_MAZEN              
    \\RIZMIJALIYATPC         
    \\RABWAH_DC              
    \\MURTAZA                
    \\MUBIAAT_PC             
    \\MAL_ASHRAF01           
    \\MAJED-PC2              
    \\KHIDMAT_ABODAWO        
    \\JAL_ZAKIR              
    \\JAL_SALAM              
    \\JAL_BULAIMI            
    \\JAL_AZIZ               
        \\JAL_AZIZ\Charity            
        \\JAL_AZIZ\C$                 Default share
        \\JAL_AZIZ\ADMIN$             Remote Admin
        \\JAL_AZIZ\print$          programs
        \\JAL_AZIZ\D$                 Default share
        \\JAL_AZIZ\IPC$               Remote IPC
    \\JAL_ABUKHALID          
    \\JAL_ABDALHAMED         
    \\JAL_ABDALAZIZ          
    \\HR-MOHAMMED            
    \\DWA_ABBAS              
    \\DAW_SAUD               
    \\DA3WA-PC               
    \\AWSOL-2                
    \\AKT_FAHD               
    \\ADWAT                  
    \\ACCOUNTI-6C370E        
        \\ACCOUNTI-6C370E\C$                 Default share
        \\ACCOUNTI-6C370E\ADMIN$             Remote Admin
        \\ACCOUNTI-6C370E\D                  
        \\ACCOUNTI-6C370E\print$             Printer Drivers
        \\ACCOUNTI-6C370E\D$                 Default share
        \\ACCOUNTI-6C370E\IPC$               Remote IPC
    \\ABDULHADI_PC           
NET
    \\FILESHARE              FileShare
        \\FILESHARE\IPC$               IPC Service (FileShare)
        \\FILESHARE\ID55375267         
        \\FILESHARE\OPENED             
        \\FILESHARE\TESTS              
        \\FILESHARE\SECURITY           
        \\FILESHARE\PUBLIC  
```

```
hostname
```
its ouput:

```
raafat-OptiPlex-780

```

---

### Post by Raafat1991 on 2013-01-25
A mistake.

---

### Post by furything on 2013-01-25
In response to irv
> I guess I didn't know that because I don't use windows any more. I  wonder if there is something like Airdroid so one could share files in a  browser between Windows, Ubuntu (or any other Linux) including   Android?
You can share files using a samba app on android and therefore files can be accessed across the network by windows and linux pcs alike.

---

### Post by furything on 2013-01-25
Hi Raafat1991

It isn't clear but if you off your firewall could you access the folders?
Not just the ip?

And have you gone through 
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by sdowney717 on 2013-01-25
What does 
iptables -L -v look like?

You see mine, I have no rules set

```
scott@scott-P5QC:~$ sudo iptables -L -v 
[sudo] password for scott: 
Chain INPUT (policy ACCEPT 3464K packets, 3761M bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 2350K packets, 2209M bytes)
 pkts bytes target     prot opt in     out     source               destination         
scott@scott-P5QC:~$ 

```

some people have to adjust name resolution order
Why, I do not know.
[http://oreilly.com/openbook/samba/book/ch07_03.html](http://oreilly.com/openbook/samba/book/ch07_03.html)
```
The global name resolve order option specifies the order of services that Samba will use in attempting name resolution. The default order is to use the LMHOSTS file, followed by standard Unix name resolution methods (some combination of /etc/hosts, DNS, and NIS), then query a WINS server, and finally use broadcasting to determine the address of a NetBIOS name. You can override this option by specifying something like the following:


[global]
    name resolve order = lmhosts wins hosts bcast
```

---

### Post by sdowney717 on 2013-01-25
[http://www.jonathanmoeller.com/screed/?p=3608](http://www.jonathanmoeller.com/screed/?p=3608)

You can run thru his examples and see if you can share a test folder.

---

### Post by Morbius1 on 2013-01-25
Edit /etc/samba/smb.conf and add a line right under the workgroup line:
```
 netbios name = raafat-780
```If you want to change the name resolve order then use this - right under the "netbios name" line:
```
name resolve order = bcast host lmhosts wins
```Then restart samba:
```
sudo service smbd restart
sudo service nmbd restart
```[COLOR=Blue][I]**Notes**:
** Samba will use the host name as the netbios name by default but yours is 4 characters too long so it's invisible to everyone on the lan. It has to be 15 characters or less.

** THe default name resolve order has bcast last so setting it to anything that also has it last won't do much good. bcast should appear first.[/I][/COLOR]

---

### Post by Raafat1991 on 2013-01-25
> **sdowney717 said:**
> [http://www.jonathanmoeller.com/screed/?p=3608](http://www.jonathanmoeller.com/screed/?p=3608)

You can run thru his examples and see if you can share a test folder.

Also no luck...

---

### Post by Raafat1991 on 2013-01-25
> **Morbius1 said:**
> Edit /etc/samba/smb.conf and add a line right under the workgroup line:
```
 netbios name = raafat-780
```If you want to change the name resolve order 

That that that all what i need to become visible on my network .

thank you man .

---

### Post by Raafat1991 on 2013-01-25
Thank you everyone i know that took a long time , thank you everyone again...

---

### Post by sudodus on 2013-01-25
I think it is very easy to install an SSH server in Ubuntu and to connect to it from other linux computers with SSH or SFTP as well as from windows computers with WinSCP. If you are happy with password authentication (should be OK in a LAN behind a router with a firewall), you can probably use the default settings of the server. Public key authentication is more secure, but not quite as easy to set up.

[[COLOR="red"]https://help.ubuntu.com/10.04/serverguide/openssh-server.html[/COLOR]]("https://help.ubuntu.com/10.04/serverguide/openssh-server.html")

"WinSCP is an open source free SFTP client, SCP client, FTPS client and FTP client for Windows. Its main function is file transfer between a local and a remote computer."

[[COLOR="Red"]http://winscp.net/eng/docs/introduction[/COLOR]]("http://winscp.net/eng/docs/introduction")

So if you feel too frustrated to connect with samba from Windows to Ubuntu, I suggest you try WinSCP - openSSH-server.

Edit: Congratulations :KS
It seems I was too late, while I was editing this post, you succeeded with Samba :-)

---

### Post by Raafat1991 on 2013-01-25
> **sudodus said:**
> I think it is very easy to install an SSH server in Ubuntu and to connect to it from other linux computers with SSH or SFTP as well as from windows computers with WinSCP. If you are happy with password authentication (should be OK in a LAN behind a router with a firewall), you can probably use the default settings of the server. Public key authentication is more secure, but not quite as easy to set up.

[[COLOR=red]https://help.ubuntu.com/10.04/serverguide/openssh-server.html[/COLOR]]("https://help.ubuntu.com/10.04/serverguide/openssh-server.html")

"WinSCP is an open source free SFTP client, SCP client, FTPS client and FTP client for Windows. Its main function is file transfer between a local and a remote computer."

[[COLOR=Red]http://winscp.net/eng/docs/introduction[/COLOR]]("http://winscp.net/eng/docs/introduction")

So if you feel too frustrated to connect with samba from Windows to Ubuntu, I suggest you try WinSCP - openSSH-server.

Edit: Congratulations :KS
It seems I was too late, while I was editing this post, you succeeded with Samba :-)

Of course i will try it (whether about what i want or not )...thank you .

---

