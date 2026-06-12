---
title: "Getting Windows to Reconize Ubuntu"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by cones on 2009-07-13
I have installed samba and have played around with the smb.conf file.  I'm trying to get ubuntu to show up on my network so my windows computers can access it.  I have a xp and a vista computer i'm trying to do this with.  I can't get ubuntu to show up on my windows network.

---

### Post by theozzlives on 2009-07-13
you should just need to change workgroup=WORKGROUP in the [global] section (unless that's the name of your workgroup). Then in Windows go to "view workgroup computers". You sure you did:```
sudo apt-get install samba
```and```
sudo smbpasswd -a username
```

---

### Post by cones on 2009-07-13
I did those but now when i try and do this ```
sudo smbpasswd -a username
``` i get "cannot locate unix account for 'username' !"
I have the work group set in the global settings for the same one as my windows computers.

---

### Post by anystupidname on 2009-07-13
Um, unless you have a user called 'username' on your system, you should substitude YOUR ACTUAL username... For example: cones

:lolflag:

---

### Post by irv on 2009-07-13
> **cones said:**
> I did those but now when i try and do this ```
sudo smbpasswd -a username
``` i get "cannot locate unix account for 'username' !"
I have the work group set in the global settings for the same one as my windows computers.
replace "username" with your name you have setup on your system.

---

### Post by cones on 2009-07-13
So that worked once i did that but my windows pc still doesn't recognize it.

---

### Post by theozzlives on 2009-07-13
Do you have a cable tester? If not try a different cable.

But first, did you go to My Network Places > View Workgroup Computers?

---

### Post by cones on 2009-07-13
I have to use a cable i was trying to do it wireless.  I did it with a cable and it didn't pick it up.

---

### Post by theozzlives on 2009-07-13
> **cones said:**
> I have to use a cable i was trying to do it wireless.  I did it with a cable and it didn't pick it up.

Unless you have a bad NIC, socket on your router, or cable if you did all those things it should connect. SAMBA is pretty easy to setup a simple peer to peer network on. Unless you're using Kubuntu.

---

### Post by cones on 2009-07-13
I tried a different plug and now i get an unknown device that i can't connect to.  I would rather have this work wireless than with a cable, can i use samba for that?

---

### Post by theozzlives on 2009-07-13
> **cones said:**
> I tried a different plug and now i get an unknown device that i can't connect to.  I would rather have this work wireless than with a cable, can i use samba for that?

Wireless? sure. Left click on Network Manager and see if any wireless networks are listed.

---

### Post by cones on 2009-07-13
> **theozzlives said:**
> Wireless? sure. Left click on Network Manager and see if any wireless networks are listed.
ok
I have the ubuntu computer hooked up to a wireless router and i have two wireless computers one is vista and the other is xp.  When i'm on my vista computer i can't pick up the ubuntu computer at all (wired or wireless) i want to be able to see the ubuntu computer wirelessly with the xp and vista computer.

---

### Post by theozzlives on 2009-07-13
Vista has problems like that (a lot of tinkering). You might be interested that not long ago Microsoft was offering Windows 7 for like $39.99 if you pre-order. I don't know if that's still the case or not but Vista is junk. I have Vista sitting in my laptop bag gathering dust and roach poop.

---

### Post by Vkec on 2009-07-13
> **theozzlives said:**
> you should just need to change workgroup=WORKGROUP in the [global] section (unless that's the name of your workgroup). Then in Windows go to "view workgroup computers". You sure you did:```
sudo apt-get install samba
```and```
sudo smbpasswd -a username
```

after i do  that i try to run it in the terminal it tells me to install samba 4

---

### Post by cones on 2009-07-13
> **theozzlives said:**
> Vista has problems like that (a lot of tinkering). You might be interested that not long ago Microsoft was offering Windows 7 for like $39.99 if you pre-order. I don't know if that's still the case or not but Vista is junk. I have Vista sitting in my laptop bag gathering dust and roach poop.
No i didn't order it i wanted to wait.  How would i get it to work on vista?

---

### Post by theozzlives on 2009-07-13
Just gotta tinker with Vista, my old computer teacher was fighting Vista when I was going to get my Certs. I'm going to the store now before it hits 105 F. Glad you can at least connect to XP.

---

### Post by irv on 2009-07-13
If you can get on the Internet with all three computers then you are networked through your router. Check all your IP address and see if you can ping them at a command prompt. If you can ping all them from each other, then you have access to them and the problem is with samba. The workgroup you have with windows and the one you have in Ubuntu must be the same. If it is "WORKGROUP" in one it must be "WORKGROUP" in the other, not "workgroup". Remember Linux is cap or not cap. It is important.

---

### Post by cones on 2009-07-13
Workgroups are the same. How do i ping them?  My two windows computers work fine together i just want to add my ubuntu one.

---

### Post by irv on 2009-07-13
> **cones said:**
> Workgroups are the same. How do i ping them?  My two windows computers work fine together i just want to add my ubuntu one.

If you put your pointer over the network icon in the panel it should show you your IP address on the Ubuntu PC. Go to a command prompt on the Windows PC and type ping IP address of the Ubuntu PC and is if you can ping it.
[ATTACH]120998[/ATTACH]

[ATTACH]120999[/ATTACH]

---

### Post by swerdna on 2009-07-13
Post the contents of your smb.conf and we might see errors. In the meantime have a look at the [global] stanza for smb.conf that works very well in a windows Ubuntu soho lan situation: [http://ubuntu.swerdna.org/ubulanprimer.html](http://ubuntu.swerdna.org/ubulanprimer.html)

---

### Post by ultimatebuster on 2009-07-13
Hi!
I'm having the same trouble. I setup Samba for printer sharing, as well as a possible file sharing on my desktop PC.
Windows 7 and Windows Vista cannot see Ubuntu, although the Workgroup is set to "WORKGROUP" (Like every other computer in the network)
 I uses a Dlink Wireless router. 

I have webmin installed so I can access Samba from there.

Edit: I just saw it in my windows network. Didn't have to set a new account!
Edit again: On XP it tells me Access Denied, unable to connect. Do I need to set up the smb account?

---

### Post by irv on 2009-07-13
> **ultimatebuster said:**
> Hi!
I'm having the same trouble. I setup Samba for printer sharing, as well as a possible file sharing on my desktop PC.
Windows 7 and Windows Vista cannot see Ubuntu, although the Workgroup is set to "WORKGROUP" (Like every other computer in the network)
 I uses a Dlink Wireless router. 

I have webmin installed so I can access Samba from there.

Edit: I just saw it in my windows network. Didn't have to set a new account!
Edit again: On XP it tells me Access Denied, unable to connect. Do I need to set up the smb account?

Just setup a user (you) in Samba.
```
sudo smbpasswd -a username
```
user name is you, so when you try to open the shared folder from windows you will be asked for this smbpassswd.

---

### Post by cones on 2009-07-14
I can ping the ubuntu computer.  I just can't get it to show on the network. Here is the smb.conf file 

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

security = user 
username map = /ect/samba/smbusers

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
```

---

