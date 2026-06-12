---
title: "SAMBA Problem: 2 Ubuntu PC's with 11.04"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by bennettg on 2011-07-15
Hello.  I am a noob, especially when it comes to networking.  I am trying to use an old laptop as a file server on my home network.  All my machines use ubuntu 11.04 and i do not have any windows machines.  there is one ipad and an android device as well.

I tried to install and configure samba on the old laptop that i want to act as a file server.  i did the following as per 
[http://www.jonathanmoeller.com/screed/?p=2143](http://www.jonathanmoeller.com/screed/?p=2143)

sudo apt-get install samba
sudo smbpasswd -a USERNAME
mkdir /home/USERNAME/test
sudo cp /etc/samba/smb.conf ~



sudo gedit /etc/samba/smb.conf then added the following to the 
very end of the file:

[test]
path = /home/USERNAME/test
available = yes
valid users = USERNAME
read only = no
browsable = yes
public = yes
writable = yes


sudo restart smbd

I can't see the server machine or the test folder on any other machines on my home network.  can anyone help?  thanks in advance

---

### Post by capscrew on 2011-07-15
> **bennettg said:**
> Hello.  I am a noob, especially when it comes to networking.  I am trying to use an old laptop as a file server on my home network.  All my machines use ubuntu 11.04 and i do not have any windows machines.  there is one ipad and an android device as well.

I tried to install and configure samba on the old laptop that i want to act as a file server.  i did the following as per 
[http://www.jonathanmoeller.com/screed/?p=2143](http://www.jonathanmoeller.com/screed/?p=2143)

sudo apt-get install samba
sudo smbpasswd -a USERNAME
mkdir /home/USERNAME/test
sudo cp /etc/samba/smb.conf ~



sudo gedit /etc/samba/smb.conf then added the following to the 
very end of the file:

[test]
path = /home/USERNAME/test
available = yes
valid users = USERNAME
read only = no
browsable = yes
public = yes
writable = yes


sudo restart smbd

I can't see the server machine or the test folder on any other machines on my home network.  can anyone help?  thanks in advance

Try adding a netbios name to the [Global] section of the smb.conf file like this :```
netbios name=<hostname of your server>
```

Edit: See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html") for an explanation.  Look for the "netbios name (G)"parameter.

---

### Post by bennettg on 2011-07-15
> **capscrew said:**
> Try adding a netbios name to the [Global] section of the smb.conf file like this :```
netbios name=<hostname of your server>
```

Edit: See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html") for an explanation.  Look for the "netbios name (G)"parameter.

is the hostname the ip address of the computer?  something like 192.168.1.4 

thanks in advance

---

### Post by capscrew on 2011-07-16
> **bennettg said:**
> is the hostname the ip address of the computer?  something like 192.168.1.4 

thanks in advance

The hostname is the name you would expect to see when browsing.  When you say this "I can't see the server machine", don't you mean the hostname?

From the terminal you can see the hostname using this command```
hostname
```

On my machine I get this```
malibu
```

It should also be the name after the @ symbol in the prompt of the terminal.  Something like *your_login@hostname*

The netbios name should be the same as your hostname unless that is mor than 15 characters.  Netbios names should be under 15 characters in length.

---

### Post by bennettg on 2011-07-17
> **capscrew said:**
> The hostname is the name you would expect to see when browsing.  When you say this "I can't see the server machine", don't you mean the hostname?

From the terminal you can see the hostname using this command```
hostname
```

On my machine I get this```
malibu
```

It should also be the name after the @ symbol in the prompt of the terminal.  Something like *your_login@hostname*

The netbios name should be the same as your hostname unless that is mor than 15 characters.  Netbios names should be under 15 characters in length.

I tried your suggestion, but it did not work.  I am so frustrated.  here is my smb.conf file....any suggestions?

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

netbios name=wgfihs

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
  workgroup = WORKGROUP

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
# parameters must be set (thanks to Ian Kahan
<<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
  passwd program = /usr/bin/passwd %u
  passwd chat = *Enter\snew\s*\spassword:* %n\n
*Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

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
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine
account" -d /var/lib/samba -s /bin/false %u

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
#       cdrom share is accesed. For this to work /etc/fstab must contain
#       an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#       is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[test]
path = /home/USERNAME/test
available = yes
valid users = USERNAME
read only = no
browsable = yes
public = yes
writable = yes

---

### Post by Bucky Ball on 2011-07-17
Personally not sure why you'd bother with Samba when no Windows machines. I use SSH and simple. Static IPs for machines, go to Places>Connect to Server, choose SSH from the drop down list, enter IP of machine you want to connect with, password and done. You can make a permanent link in 'Places' for the connection so you don't need to do that everytime. 

Suits me as I find it simpler to set up but might not suit you, naturally. ;)

---

### Post by bennettg on 2011-07-17
> **Bucky Ball said:**
> Personally not sure why you'd bother with Samba when no Windows machines. I use SSH and simple. Static IPs for machines, go to Places>Connect to Server, choose SSH from the drop down list, enter IP of machine you want to connect with, password and done. You can make a permanent link in 'Places' for the connection so you don't need to do that everytime. 

Suits me as I find it simpler to set up but might not suit you, naturally. ;)

I have other devices on the network: android phones and a roku box.  In order for the roku to see files on the computer, I need to use samba.  Do you have any suggestions on a step-by step guide?   i tried the ubuntu community documentation, but it resulted in the problems above.

thanks in advance

---

### Post by Bucky Ball on 2011-07-17
> **bennettg said:**
> I have other devices on the network: android phones and a roku box.  In order for the roku to see files on the computer, I need to use samba.

Roger that. ;)

---

### Post by capscrew on 2011-07-17
> **bennettg said:**
> I tried your suggestion, but it did not work.  I am so frustrated.  here is my smb.conf file....any suggestions?
```

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which
# are not shown in this example
#...

[global]

netbios name=wgfihs

...

[test]
path = /home/USERNAME/test
available = yes
valid users = USERNAME
read only = no
browsable = yes
public = yes
writable = yes

```


I think there should be spaces between the '=' sign.  This was my mistake.  It should look like this```
netbios name = wgfihs
```

Try that and see if you can see the machine "wgfihs" by browsing.

Can you ping this host from the command line?```
ping wgfihs
```

---

### Post by bennettg on 2011-07-17
> **capscrew said:**
> I think there should be spaces between the '=' sign.  This was my mistake.  It should look like this```
netbios name = wgfihs
```

Try that and see if you can see the machine "wgfihs" by browsing.

Can you ping this host from the command line?```
ping wgfihs
```

Thank you very much for fixing my machine :-).  Good Karma will come to you.

EDIT: It stopped working after I rebooted the machine and i can lo longer ping it./......what did i do wrong???? please help

---

### Post by bennettg on 2011-07-17
> **bennettg said:**
> Thank you very much for fixing my machine :-).  Good Karma will come to you.

EDIT: It stopped working after I rebooted the machine and i can lo longer ping it./......what did i do wrong???? please help

It stopped working after I rebooted the machine and i can lo longer ping it./......what did i do wrong???? please help

---

### Post by capscrew on 2011-07-18
> **bennettg said:**
> It stopped working after I rebooted the machine and i can lo longer ping it./......what did i do wrong???? please help

My guess is you did nothing wrong.  Sometimes the nmbd (name service) process fails to load.  From the command line you can list the Samba processes using this ```
pgrep -l mbd
```

Id you get back something like this ```
pgrep -l mbd
960 smbd
1064 smbd

```

Then the nmbd process is not running.  You can start it like this```
sudo service nmbd start 
[sudo] password for <user>: 
nmbd start/running, process 1764

```

Then it should look like this
```
pgrep -l mbd
960 smbd
1064 smbd
[COLOR="Red"]**1764 nmbd**[/COLOR]

```

---

### Post by idlemind324 on 2011-07-18
Have you restarted the samba service since rebooting?

---

