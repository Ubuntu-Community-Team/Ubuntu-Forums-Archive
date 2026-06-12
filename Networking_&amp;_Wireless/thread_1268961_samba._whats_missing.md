---
title: "samba. whats missing"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by ken_ver_2.5 on 2009-09-17
so this is my first post on my new linux box running ubuntu 904.
Sorry for the spelling as I haven't found a spell checker yet..


so heres the problem I have windows boxes on the net work.
from the linux box I can see and tranfer files.
from the windows box nothing shows up.
my guess is that I am missing something in my samb.conf file.

heres a cp

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
log file = file:///var/log/samba/log.%25m

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
encrypt passwords = yes

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
passwd program = file:///usr/bin/passwd%20%25u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
map to guest = Bad User

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

wins support = no
restrict anonymous = no
domain master = no
netbios name = linbox1
logon home = %5C%5C%25N%5C%25U
smb passwd file = file:///etc/samba/smbpasswd
pid directory = file:///var/run/samba
logon path = %5C%5C%25N%5C%25U%5Cprofile
private dir = file:///etc/samba

[printers]
comment = All Printers
browseable = no
path = /var/spool/samba
printable = yes
create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
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


[ken]
path = /home/ken
guest ok = yes
read only = no

any idea what I am missing?

---

### Post by Iowan on 2009-09-17
Have you installed Samba (the server component)? The client component comes pre-installed.  Have you used smbpasswd to create a user (ken?)?

---

### Post by ken_ver_2.5 on 2009-09-17
I think its installed. not sure where to find it.
there are two users and one folder shared.
I set up samba through system settings advanced tab
as root using the kde desktop.
I think I am a lil confused here. did view the how to guide.
but not real sure what it all means

---

### Post by Iowan on 2009-09-17
From a terminal try:```
ps -ef |grep mbd
```You should see some lines with smbd or nmbd - otherwise, Samba isn't running.

---

### Post by ken_ver_2.5 on 2009-09-17
this is what I get.

ken@ken-desktop:~$ ps -ef |grep mbd
ken       3272  3255  0 18:31 pts/1    00:00:00 grep mbd
ken@ken-desktop:~$

thanks for your help btw.

---

### Post by Iowan on 2009-09-17
Try starting it:```
sudo /etc/init.d/samba start
```If you get a "not found" error, you may need to install the server. Otherwise (or "but first"), try running **testparm** to check for errors in */etc/samba/smb.conf*.

---

### Post by ken_ver_2.5 on 2009-09-17
this is what I get.


ken@ken-desktop:~$ sudo /etc/init.d/samba start
[sudo] password for ken:
 * Starting Samba daemons                                                [ OK ]
ken@ken-desktop:~$

so what do I need to install?
in synaptic package manger
it shows other components but
I am not sure what to install. 

Am I mistaken that its something not set right in the smb file?
this is not my first linux but have always been confused about
this file.

---

### Post by Iowan on 2009-09-17
Try this again:```
ps -ef |grep mbd
```See if some lines with smbd or nmbd show up now. Another thing to try:```
sudo /etc/init.d/samba status
``` I discovered (the hard way) that it's important to use **sudo**.

---

### Post by ken_ver_2.5 on 2009-09-18
Back for another day of fun.

I input what you posted this is what I got.



ken@ken-desktop:~$ sudo /etc/init.d/samba start
[sudo] password for ken:
 * Starting Samba daemons                                                [ OK ]
ken@ken-desktop:~$ ps -ef |grep mbd
ken       3364  3274  0 07:34 pts/1    00:00:00 grep mbd
ken@ken-desktop:~$ sudo /etc/init.d/samba status
 * nmbd is not running
 * smbd is not running
ken@ken-desktop:~$

so I started samba [ok]
and its not running.

Now I am really confused.
Shouldn't samba start automatically?

---

### Post by adok on 2009-09-18
i believe theres something missing in your installation.

this is the output of the above commands from previous posts:

```

adok@valakas:~$ ps -ef |grep mbd
root     19996     1  0 13:18 ?        00:00:00 /usr/sbin/nmbd -D
root     20000     1  0 13:18 ?        00:00:00 /usr/sbin/smbd -D
root     20004 20000  0 13:18 ?        00:00:00 /usr/sbin/smbd -D
adok     20494 20475  0 13:24 pts/0    00:00:00 grep mbd

adok@valakas:~$ sudo /etc/init.d/samba status
 * nmbd is running
 * smbd is running

```

would be better to read this good guide about samba on ubuntu [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by ken_ver_2.5 on 2009-09-18
thanks guess I need to do some more reading.
I really broke it now lol.
loaded smb4 oops that didn't work.
but your right something is missing.

---

### Post by ken_ver_2.5 on 2009-09-18
I guess you have to screw everything up to fix it :)
I uninstalled all samba then re installed it.
I ran the commands and now get this.



ken@ken-desktop:~$ sudo /etc/init.d/samba start
 * Starting Samba daemons                                                [ OK ]
ken@ken-desktop:~$ ps -ef |grep mbd
root      3539     1  0 08:45 ?        00:00:00 /usr/sbin/nmbd -D
root      3543     1  0 08:45 ?        00:00:00 /usr/sbin/smbd -D
root      3546  3543  0 08:45 ?        00:00:00 /usr/sbin/smbd -D
ken       3606  3569  0 08:49 pts/1    00:00:00 grep mbd
ken@ken-desktop:~$ sudo /etc/init.d/samba status
 * nmbd is running
 * smbd is running
ken@ken-desktop:~$



I can now see my share from the other computers.
thank you for all your help.
now if it all works when I reboot I can move on to the other issues.

---

