---
title: "Playing DVD across network with SAMBA - won't work"
date: 2010-07-16
forum: Multimedia Software
---

### Post by zcacogp on 2010-07-16
Chaps, 

I'm trying to play a DVD across a wireless network. The DVD is in one machine (desktop - address 192.168.10.3), and I'm trying to play it in a laptop (x61s - address 192.168.10.21). The DVD will play fine on the desktop (open Nautilus and click "Open Movie Player"), but it won't play on the laptop. 

The drive (DVD) is mapped on the laptop as a Samba share, and I can see the disk and open it in Nautilus, and can see all the files within it (i.e. it appears to read fine). However when I click on "Open Movie Player", Movie Player opens but produces a window saying "An error occurred. Could not read from resource". 

If I try opening it with VLC then it won't open either. The VLC window gets a little wider for a few moments but that's about it. If I open VLC from a terminal then I get the following message in the terminal when I try to open the DVD from the network: 

```
ogp@ogp-X61s:~$ vlc
VLC media player 1.0.6 Goldeneye
[0x9792668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device //192.168.10.3/DVD mounted on /media/dvd for CSS authentication
libdvdread: Could not open //192.168.10.3/DVD with libdvdcss.
libdvdread: Can't open //192.168.10.3/DVD for reading
libdvdread: Device //192.168.10.3/DVD inaccessible, CSS authentication not available.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/ogp/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4
[0xb741d590] main input error: ES_OUT_RESET_PCR called
[0xb741d590] main input error: ES_OUT_RESET_PCR called
[0xb741d590] main input error: ES_OUT_RESET_PCR called
[0xb741d590] main input error: ES_OUT_RESET_PCR called
ogp@ogp-X61s:~$ 
```

This suggests (to my understanding) something similar - for some reason, it cannot open the DVD across the network. 

I have tried this with the network running wirelessly and with it with the network cable plugged in, and it produces the same results. Both machines are running 10.04 lucid, and both are updated. I've followed all the steps in this: 

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

(The comprehensive multimedia how-to), and didn't get any errors at any stage. But it still doesn't work. 

Last point - I'm just getting out of the 'beginner' stages, so go a little easy if things get a bit technical! Thanks!

All help appreciated. Thanks in advance. 


Oli.

---

### Post by zcacogp on 2010-07-29
Anyone? 

Should it help, here is the smb.conf file from the sever (with the DVD drive): 

```
[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = lbbarnet

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
   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.

   encrypt passwords = true
   username map = /etc/samba/smbusers

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
   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups

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
   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no

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
   browseable = yes
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

# Drive sharing bit.

[dvd]
   comment = Samba server's DVD drive
   read only = no
   locking = no
   path = /media/dvd
   guest ok = no


[Helena]
   comment = Helena on Desktop
   read only = no
   locking = no
   path = /media/Helena
   guest ok = no

[Ianthe]
   comment = Ianthe on Desktop
   read only = no
   locking = no
   path = /media/Ianthe
   guest ok = no




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
And here is the fstab file for the client machine: 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc   proc    nodev,noexec,nosuid     0       0
/dev/sda8       /       ext3    errors=remount-ro       0       1
/dev/sda5       /media/Horatio  ntfs-3g defaults,locale=en_GB.utf8      0      $
/dev/sda6       /media/Ieuan    ntfs-3g defaults,locale=en_GB.utf8      0      $
/dev/sda7       none    swap    sw      0       0

//192.168.10.3/Ianthe /media/Ianthe cifs credentials=/etc/samba/user,noexec 0 0

//192.168.10.3/Helena /media/Helena cifs credentials=/etc/samba/user,noexec 0 0


//192.168.10.3/DVD /media/dvd cifs credentials=/etc/samba/user,noexec 0 0

```

All help welcomed - thanks. 


Oli.

---

### Post by aeiah on 2010-07-29
```

libdvdread: Device //192.168.10.3/DVD inaccessible, CSS authentication not available.

```

can this laptop play dvds locally?

also, even if you do get it working, are you sure your wireless network is up to the task? DVDs push a lot of data, and if you're on a wireless g network it may struggle to keep up. 

i can mostly stream xvid and H.264 video over wireless g, using mediatomb upnp server and xbmc on my netbook, for the record

---

### Post by zcacogp on 2010-07-29
Aeiah, 

Thanks for your answer. 

The lappie has no DVD drive (no CD drive either), but it has played DVD's fine over the network previously, using a Windows-to-windows network. 

I guess that answers the question about the data carrying capacity of the wireless as well. 

Thanks for your help. 


Oli.

P.S. On re-reading, this post sounds a little dismissive. It's not meant to be - sorry!

---

### Post by aeiah on 2010-07-29
i guess you should check to see if your laptop's ubuntu install has dvd playback abilities. there's a stickied thread in this sub-forum that can guide you through getting dvd playback installed. it isn't available by default due to legal issues in certain countries.

---

### Post by Morbius1 on 2010-07-29
I've never tried to access a cd/dvd across the network but looking at the share definition for the drive there may be a problem with linux permissions and not samba:
> [dvd]
   comment = Samba server's DVD drive
   read only = no
   locking = no
   path = /media/dvd
   guest ok = no
When you insert a dvd it will automatically mount with you as owner with read / write access to you and no access to anyone else. One way around this is to add a line to the share definition that will convert the remote user to you ( after they have provided the correct credentials to samba for access ) . The resulting share definition would look like this:
> [dvd]
   comment = Samba server's DVD drive
   read only = no
   locking = no
   path = /media/dvd
[COLOR=Blue]   force user = morbius[/COLOR]
   guest ok = no
[COLOR=Blue]*Changing morbius to whatever your local login user name is on the box that has the dvd player.*[/COLOR]

---

### Post by zcacogp on 2010-07-29
Aeiah, 

I've installed pretty much everything people seem to list as essentials to make DVD's play on a machine, on the laptop. I *think *I'm OK on this front, but thanks for suggesting it. 

Morbius,

Now that's an interesting suggestion, thanks. I'll give that a go. To clarify, I log into the desktop as 'ogp', therefore the added line has to be 'forceuser = ogp' - non? 

Does the fact that I log into the laptop as 'ogp' as well make any difference to this? 

(I am aware that there are also Samba accounts, seperate to the machine log in accounts, and part of setting up the Samba login involved setting up the Samba account on the Desktop. I don't fully understand what I did at this stage, just followed the instructions ... is there a good on-line explanation of the different accounts and how they work together?)

Thanks for the suggestion. I'll report back once I have tried it (probably later on this afternoon - I'm not at the machines in question at the moment.) 


Oli.

---

### Post by Morbius1 on 2010-07-29
> To clarify, I log into the desktop as 'ogp', therefore the added line has to be 'forceuser = ogp' - non? 
Make sure you get the syntax right, it should be:
```
force user = ogp
```>  Does the fact that I log into the laptop as 'ogp' as well make any difference to this? In this particular case the "force user" option refers to what Samba calls the "UNIX user name". That means the local login user - i.e., ogp. You don't have to create a samba user ( smbpasswd ) for that user to have this work.

---

### Post by zcacogp on 2010-07-29
Morbius, 

Well, it didn't work the first time, but after a restart or two (not sure why this was necessary), it has. It works. I can play DVD's across the wireless network, from machine to machine! 

Having said that, it does struggle over the wireless a little (as you suggested, aeiah - thanks), and it seems to want to buffer almost all of the disk before playing it. As in, you can open the root menu of the DVD easily, and click "Play Film" (or whatever), but it then hangs for a long time, with a very large amount of network traffic, before going ahead and playing the disk. Why is this? 

Thanks very much for your input chaps. I am very pleased this is working!


Oli.

---

