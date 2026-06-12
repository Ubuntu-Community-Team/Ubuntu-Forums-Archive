---
title: "Cannot mount samba shares on Ubuntu"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by jbowen7 on 2010-02-04
I just set up my first web server at home on ubuntu 9.10 server edition, and decided to install another hard drive to the server, mounted at /media/storage, so that I could have a home file sharing server for everyone on my local network. The drive is formatted fat32 so my friends with xp wouldn't have issues reading/writing to the share, and the workgroup = MSHOME.

The problem is everyone can use this share except me; mac osx and xp computers read/write, mount, etc. just fine, but my ubuntu desktop 9.10 is refusing ("Unable to mount Location, Failed to receive share list from server").

So far I have done:
1) install samba smbfs smbclient
2) edited /etc/samba/smb.conf
     i) changed workgroup = MSHOME
    ii) added netbios name = (name of computer I'm trying to access from, client)
   iii) uncommented and changed: name resolve order = lmhost wins bcast host
3) edited /etc/nsswitch.conf by adding wins
     i) hosts:                 files mdns4_minimal [NOT FOUND = return] wins dns mdns4    
4) installed winbind

Furthermore, there is no firewall enabled on either machine.
Any suggestions are greatly appreciated, thanks.

cat /etc/nsswitch.conf produces:

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis




cat /etc/samba/smb.conf produces:

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
   workgroup = MSHOME
   netbios name = Lord-Gardaq

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
   name resolve order = lmhosts host wins bcast 

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

---

### Post by Iowan on 2010-02-04
You have probably seen [this]("http://ubuntuforums.org/showthread.php?t=1169149") How-To.
Have you set up a Samba user/password?

---

### Post by jbowen7 on 2010-02-04
Iowan,

No I didn't setup username/passwd for samba. On the server I've have this appended to the end of /etc/samba/smb.conf:

[storage]
comment = this is public storage
path = /media/storage
public = yes
writable = yes
create mask = 0777
directory mask = 0777
guest = ok
force users = nouser
force group = nogroup

I'm able to access the share from the other two computers (mac osx, xp) without a login or password.

---

### Post by jbowen7 on 2010-02-05
I'm still working away at this problem, but I can't seem to solve it.
Anyone have suggestions?

---

### Post by dmizer on 2010-02-06
Below where it says:
```
# security = user
```
Add this line:
```
security = share
```

In the "MISC" section, add these lines:
```
domain master = yes
local master = yes
preferred master = yes
os level = 65
```

Change your share stanza to this:
```
[storage]
comment = this is public storage
path = /media/storage
read only = no
guest ok = yes
force user = [COLOR="Red"]ubuntu-username[/COLOR]
force group = [COLOR="Red"]ubuntu-username[/COLOR]
```
Where "[COLOR="Red"]ubuntu-username[/COLOR]" should be replaced with the username you use to log into your samba server with.

Finally, shut down all the machines on your network (including the server), then start the server, wait until it boots and then start the rest of the computers.

See if that fixes your problem.

As an asside (and for future reference), you should not have formatted your drive to fat32. The only time you need to worry about the file system is when both Windows and Ubuntu reside on the same computer (as with a dual boot situation) and you want to share a common partition between them. You should have used either ext3 or ext4, as these file systems do not have a 2GB file size limit.

---

### Post by jbowen7 on 2010-02-06
dmizer,

I got really frustrated so I started all over..
I reformatted sdb1 as ext3 because everytime i tried # mkfs.ntfs /dev/sdb1 , it would finish the format but when I ran fdisk -l the system type for this was linux. But I was worried about the windows computer being able to write to ext3.

Now I wanted anyone on the local network to able to access this share without having linux accounts or samba accounts. Your steps are only necessary for samba users, no?

Thanks dmizer..
When I finish this process I will do a write up to recreate my setup.

---

### Post by jbowen7 on 2010-02-06
I was having permissions issues where the hard drive was mounted /media/Storage and though I was modifying fstab to mount rw, I was still having difficulty writing to it, so I created another folder inside the mount and changed the permissions. It works now.. but I'm back to my original problem:
I can't access the share on my ubuntu desktop via network places, but I can ftp in...
 This is what I did to get it working:
 Sharing second hard disk (sdb1) on the network:
 1) install hard disk
  i) find out what it's called :# sudo fdisk -l
  ii) create partition on disk: # fdisk /dev/sdb
  iii) format disk: # sudo mkfs -t ext3 /dev/sbd1
 2) mount hard disk
  i) make directory for disk to be mounted, ex. # sudo mkdir /media/sdb1
  ii) change permissions on directory: # sudo chmod 777 /media/storage
  iii) mount drive on that dir: # sudo mount /dev/sdb1 /media/sdb1
  iv) make drive automatically mounted by editing fstab:
   a) # sudo pico /etc/fstab
   b) add 'dev/sdb1 /media/storage ext3 defaults 0 0' to end of file
   c) write then exit
 3) install samba to enable sharing
  i) # sudo apt-get install samba smbclient smbfs
 4) reboot
 5) make another directory in /media/sbd1, example /media/sbd1/Storage
 i) change permissions: # chmod 777 /media/sbd1/Storage
 6) configure samba to share with network computers
  i) # sudo pico /etc/samba/smb.conf
  ii) add this (below)
 [storage]
 comment = this is public storage
 path = /media/sbd1/Storage
 public = yes
 writable = yes
 create mask = 0777
 directory mask = 0777
 guest = ok
 6) Misc
 i) to increase perfomance of share, uncomment in the misc section of smb.conf:
  a) SO_RCVBUF=8192 SO_SNDBUF=8192        (and add this to the socket options line) 
  b) socket options = TCP_NODELAY                 (line should look like this: socket options = TCP_NODELAY  SO_RCVBUF=8192 SO_SNDBUF=8192)  
7) reboot
 NOTES::
1) Make sure the domain names are the same and change the smb.conf accordingly

---

### Post by dmizer on 2010-02-08
This ...
> **jbowen7 said:**
>  i) to increase perfomance of share, uncomment in the misc section of smb.conf:
  a) SO_RCVBUF=8192 SO_SNDBUF=8192
  b) socket options = TCP_NODELAY

Should look like this:
```
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
```

---

### Post by jbowen7 on 2010-02-08
Thanks dmizer,

I didn't catch that. It's strange that the default smb.conf is written with 
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
on two separate lines..

Thanks for catching it,

johnny

---

